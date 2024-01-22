<script setup>
    document.addEventListener('DOMContentLoaded', function () {
    const loginForm = document.getElementById('loginForm');
    const loginButton = document.getElementById('loginButton');

    loginButton.addEventListener('click', function () {
        // Execution of form validation
        if (validateForm()) {
            // Switching the Button to "Charging"
            loginButton.innerHTML = '<svg aria-hidden="true" role="status" class="inline w-4 h-4 me-3 text-white animate-spin" viewBox="0 0 100 101" fill="none" xmlns="http://www.w3.org/2000/svg"><path d="M100 50.5908C100 78.2051 77.6142 100.591 50 100.591C22.3858 100.591 0 78.2051 0 50.5908C0 22.9766 22.3858 0.59082 50 0.59082C77.6142 0.59082 100 22.9766 100 50.5908ZM9.08144 50.5908C9.08144 73.1895 27.4013 91.5094 50 91.5094C72.5987 91.5094 90.9186 73.1895 90.9186 50.5908C90.9186 27.9921 72.5987 9.67226 50 9.67226C27.4013 9.67226 9.08144 27.9921 9.08144 50.5908Z" fill="#E5E7EB"/><path d="M93.9676 39.0409C96.393 38.4038 97.8624 35.9116 97.0079 33.5539C95.2932 28.8227 92.871 24.3692 89.8167 20.348C85.8452 15.1192 80.8826 10.7238 75.2124 7.41289C69.5422 4.10194 63.2754 1.94025 56.7698 1.05124C51.7666 0.367541 46.6976 0.446843 41.7345 1.27873C39.2613 1.69328 37.813 4.19778 38.4501 6.62326C39.0873 9.04874 41.5694 10.4717 44.0505 10.1071C47.8511 9.54855 51.7191 9.52689 55.5402 10.0491C60.8642 10.7766 65.9928 12.5457 70.6331 15.2552C75.2735 17.9648 79.3347 21.5619 82.5849 25.841C84.9175 28.9121 86.7997 32.2913 88.1811 35.8758C89.083 38.2158 91.5421 39.6781 93.9676 39.0409Z" fill="currentColor"/></svg>Loading...';

            // Simulation of asynchronous operation - 5 seconds
            setTimeout(function () {
                // Change the button back to its original state
                loginButton.innerHTML = 'Login';
            }, 5000);
        }
    });

    function validateForm() {
        const username = document.getElementById('username').value;
        const password = document.getElementById('password').value;
        const usernameError = document.getElementById('usernameError');
        const passwordError = document.getElementById('passwordError');

        // Reset error messages
        usernameError.textContent = '';
        passwordError.textContent = '';

        // Validate username or email
        if (!username || username.length < 6 || username.length > 50) {
            usernameError.textContent = 'Username or email must be between 6 and 50 characters';
            return false;
        }

        // Validate password
        const passwordRegex = /^(?=.*[A-Za-z])(?=.*\d)(?=.*[@$!%*#?&])[A-Za-z\d@$!%*#?&]{10,}$/;
        if (!password || !passwordRegex.test(password)) {
            passwordError.textContent = 'Password must be at least 10 characters and contain at least 1 alphabet, 1 symbol, and 1 number';
            return false;
        }

        return true;
    }
});


</script>

<template>
  <body class="min-h-screen flex items-center justify-center">
    
      <!-- Main Card -->
      <!-- Content card -->
      <div class="max-w-2xl w-full gap-4 grid grid-col md:grid-cols-2 shadow-md">

          <!-- icon "or" -->
          <div class="bg-black text-white absolute mt-[240px] md:mt-2 left-1/2 transform -translate-x-7 rounded-full p-4 md:p-4">
              <p class="pl-1 pr-1">or</p>
          </div>


          <!--Logo facebook -->
          
          <div class="flex items-center justify-center flex-col bg-blue-900">
              <svg class="p-5 md:p-0" fill="#ffffff" height="200px" width="200px" version="1.1" id="Layer_1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" viewBox="0 0 310 310" xml:space="preserve" stroke="#ffffff"><g id="SVGRepo_bgCarrier" stroke-width="0"></g><g id="SVGRepo_tracerCarrier" stroke-linecap="round" stroke-linejoin="round"></g><g id="SVGRepo_iconCarrier"> <g id="XMLID_834_">
                  <path id="XMLID_835_" d="M81.703,165.106h33.981V305c0,2.762,2.238,5,5,5h57.616c2.762,0,5-2.238,5-5V165.765h39.064 c2.54,0,4.677-1.906,4.967-4.429l5.933-51.502c0.163-1.417-0.286-2.836-1.234-3.899c-0.949-1.064-2.307-1.673-3.732-1.673h-44.996 V71.978c0-9.732,5.24-14.667,15.576-14.667c1.473,0,29.42,0,29.42,0c2.762,0,5-2.239,5-5V5.037c0-2.762-2.238-5-5-5h-40.545 C187.467,0.023,186.832,0,185.896,0c-7.035,0-31.488,1.381-50.804,19.151c-21.402,19.692-18.427,43.27-17.716,47.358v37.752H81.703 c-2.762,0-5,2.238-5,5v50.844C76.703,162.867,78.941,165.106,81.703,165.106z"></path>
                  </g> </g>
              </svg>
              <h5 class="block text-white text-sm mt-2 md:mt-5 md:mb-0 mb-8">Connect with Facebook</h5>
          </div>

              
          <!-- Form -->
          <div class="p-10 bg-gray-900">
              <h2 class="text-2xl font-semibold text-white text-center mb-5">Login</h2>
  
              <form id="loginForm">
                  <!-- Username or Email -->
                  <div class="mb-4">
                      <label for="username" class="block text-gray-700 text-sm font-bold mb-2">Username or Email</label>
                      <input type="text" id="username" name="username" class="w-full px-3 py-2 border rounded-md focus:outline-none focus:border-blue-500" placeholder="Enter your username or email">
                      <div id="usernameError" class="text-red-500 text-xs mt-1"></div>
                  </div>
                      
                  <!-- Password -->
                  <div class="mb-4">
                      <label for="password" class="block text-gray-700 text-sm font-bold mb-2">Password</label>
                      <input type="password" id="password" name="password" class="w-full px-3 py-2 border rounded-md focus:outline-none focus:border-blue-500" placeholder="Enter your password">
                      <a href="#" class="underline text-gray-500 text-sm mt-2">Forgot your password?</a>
                      <div id="passwordError" class="text-red-500 text-xs mt-1"></div>
                  </div>

                  <!-- Login Button -->
                  <button type="button" id="loginButton" class="hover:bg-blue-900 w-full md:mb-0 mb-5 bg-blue-800 text-white py-2 rounded-md focus:outline-none focus:bg-blue-600 zoom">  
                    Login
                  </button>
                  
                    <!-- icon arrow -->
                    
                    <div class="bg-orange-700 text-white absolute drop-shadow-2xl shadow-black top-1/2 left-1/2 mt-[320px] ml-[-40px] md:ml-[310px] md:-mt-0 xl:-mt-10 rounded-full p-2">                        
                        <svg width="64px" height="64px" viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg" stroke="#ffffff"><g id="SVGRepo_bgCarrier" stroke-width="0"></g><g id="SVGRepo_tracerCarrier" stroke-linecap="round" stroke-linejoin="round"></g><g id="SVGRepo_iconCarrier"> <path d="M6 12H18M18 12L13 7M18 12L13 17" stroke="#ffffff" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"></path> </g></svg>
                    </div>

              </form>
          </div>

      </div>
      
  </body>
</template>

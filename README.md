<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>liquid.vape</title>
    <style> /* General body and HTML styling */
        html,
        body {
            font-family: Arial, Helvetica, sans-serif;
            width: 100%;
            height: 100%;
            background-color: rgb(255, 255, 255);
            margin: 0;
            padding: 0;
            display: flex;
            flex-direction: column;
            align-items: center;
      }

   {
            padding: 0;
            margin: 0;
            box-sizing: border-box; /* Added for better layout control */
        }
        h1 {
            font-size: 40px;
            letter-spacing: 5px;
            font-style: italic;
            font-weight: bold;
            text-shadow: 2px 2px 4px #000; /* Added default shadow offsets and blur */
            margin-top: 20px;
            text-align: center;
        }
        .button {
            min-width: 120px;
            position: relative;
            cursor: pointer;
            padding: 12px 17px;
            border: 0;
            border-radius: 7px;
            box-shadow: inset 0 0 0 1px rgba(255, 255, 255, 0.1);
            background: radial-gradient(
                ellipse at bottom,
                rgb(255, 255, 255) 0%, /* Assuming this was meant for a different button or needs color adjustment */
                rgb(255, 255, 255) 45% /* Will likely make text invisible if button bg is white and text is light */
            );
            /* Defaulting to a darker button color for visibility with light text */
            background: radial-gradient(
                ellipse at bottom,
                #555 0%,
                #333 45%
            );
            color: rgba(255, 255, 255, 0.66);
            transition: all 1s cubic-bezier(0.15, 0.83, 0.66, 1);
        }
        .button::before {
            content: "";
            width: 70%;
            height: 1px;
            position: absolute;
            bottom: 0;
            left: 15%;
            background: rgb(255, 255, 255);
            background: linear-gradient(
                90deg,
                rgba(255, 255, 255, 0) 0%,
                rgba(255, 255, 255, 1) 50%,
                rgb(247, 241, 241) 100%
            );
            opacity: 0.2;
            transition: all 1s cubic-bezier(0.15, 0.83, 0.66, 1);
        }

   .button:hover {
            color: rgb(255, 255, 255, 1);
            transform: scale(1.1) translateY(-3px);
        }

  .button:hover::before {
            opacity: 1;
        }

  /* InputContainer - Note: This seems to be for a different input style than the one used in the HTML */
        /* Keeping it for now, but it might be unused or conflicting */
        .InputContainer {
            width: 1330px; /* This is very wide, will need media queries */
            max-width: 90%; /* Added for responsiveness */
            height: 50px;
            display: flex;
            align-items: center;
            justify-content: center;
            background: linear-gradient(to bottom,rgb(227, 213, 255),rgb(255, 231, 231));
            border-radius: 30px;
            overflow: hidden;
            cursor: pointer;
            box-shadow: 2px 2px 10px rgba(0, 0, 0, 0.075);
            margin-top: 20px; /* Added margin */
        }

   .input { /* This class is also used for the search bar, may conflict */
            width: 1300px; /* This is very wide, will need media queries */
            max-width: calc(100% - 30px); /* Added for responsiveness */
            height: 40px;
            border: none;
            outline: none;
            caret-color: rgb(255, 81, 0);
            background-color: rgb(255, 255, 255);
            border-radius: 30px;
            padding-left: 15px;
            letter-spacing: 0.8px;
            color: rgb(19, 19, 19);
            font-size: 13.4px;
        }

   /* Search bar specific styling (from the second CSS block) */
        .searc { /* Container for the search input */
            display: flex; /* Added for centering */
            justify-content: center; /* Added for centering */
            align-items: center; /* Added for centering */
            margin-top: 20px; /* Added margin */
            margin-bottom: 20px; /* Added margin */
            width: 100%;
        }

 .searc input[type="text"] {
            position: relative; /* Changed from absolute for better flow */
            /* top: 50%; */ /* Removed, handled by flexbox in .searc */
            /* left: 50%; */ /* Removed, handled by flexbox in .searc */
            /* transform: translate(-50%, -50%); */ /* Removed */
            color: #000000;
            font-size: 16px;
            background: transparent;
            width: 25px; /* Initial width for icon */
            height: 25px; /* Initial height for icon */
            padding: 10px;
            border: 3px solid #9a86fb;
            outline: none;
            border-radius: 35px;
            transition: all 0.5s;
            box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2),
                        0 6px 20px 0 #9a86fb;
            text-indent: -9999px; /* Hide text initially, show placeholder on focus */
        }

.searc input[type="text"]::before { /* This won't work directly on input, using placeholder */
            /* content: "🔍"; */ /* Handled by placeholder and potentially background image */
            /* position: absolute; */
            /* left: 10px; */
            /* font-size: 16px; */
            /* color: #9a86fb; */
            /* transition: opacity 0.5s; */
        }

  .searc input[type="text"]:focus::before {
            /* opacity: 0; */
        }

   .searc input[type="text"]::placeholder {
            color: #000000;
            opacity: 1; /* Make placeholder (icon) visible initially */
            transition: opacity 150ms ease-out;
            text-indent: 0; /* Show placeholder text */
        }

  .searc input[type="text"]:focus::placeholder {
            opacity: 1;
        }

   .searc input[type="text"]:focus,
        .searc input[type="text"]:not(:placeholder-shown):not(:focus) { /* Keep expanded if text entered */
             width: 250px;
             box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2),
                         0 6px 20px 0 #FFBB70;
             text-indent: 0; /* Show text when expanded */
        }

   .searc input[type="text"]:hover {
            box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2),
                        0 6px 20px 0 #cca4df;
        }


  /* Product container and product styling */
        .product-container {
            display: flex;
            flex-wrap: wrap;
            justify-content: center;
            gap: 20px;
            padding: 20px;
            margin-top: 20px;
            overflow: auto; /* Changed from overflow:auto to overflow-y: auto for vertical scroll only if needed */
            overflow-y: auto;
            width: 100%; /* Ensure it takes full width */
            max-height: 70vh; /* Adjusted for better viewing with header and footer */
        }

   .product {
            width: 200px;
            padding: 10px;
            border: 1px solid #ddd;
            border-radius: 10px;
            text-align: center;
            background-color: #f8f8f8;
            text-decoration: none; /* Remove underline from link */
            color: inherit; /* Inherit text color */
        }
        .product a { /* Styling for the anchor tag wrapping product */
            text-decoration: none;
            color: inherit;
            display: block; /* Make the link fill the product div */
        }
        .product img {
            width: 100%;
            height: auto;
            max-height: 150px; /* Added max-height for consistency */
            object-fit: cover; /* Ensure images cover the area well */
            border-radius: 5px;
        }
        .product h2 {
            font-size: 16px;
            margin: 10px 0;
        }
        .product p {
            font-size: 14px;
            color: #333;
        }
        /* Social media icons styling */
        ul {
            list-style: none;
            padding: 0; /* Reset padding for ul */
        }
        .example-2 {
            display: flex;
            /* justify-content: center ; */ /* Already centered by body's align-items */
            /* align-items: center ; */ /* Already centered by body's align-items */
            /* flex-direction: column; */ /* This makes them stack vertically, let's make them row for horizontal display */
            flex-direction: row; /* Horizontal display */
            justify-content: center; /* Center icons horizontally */
            align-items: center;
            row-gap: 0.5rem; /* Will become column-gap with flex-direction: row */
            column-gap: 0.5rem;
            margin-top: 30px; /* Added margin */
            margin-bottom: 30px; /* Added margin */
            width: 100%; /* Take full width */
        }
        .example-2 .icon-content {
            margin: 0 10px;
            position: relative;
        }
        .example-2 .icon-content .tooltip {
            position: absolute;
            top: -30px; /* Adjusted for better positioning above icon */
            left: 50%;
            transform: translateX(-50%);
            color: #fff;
            padding: 6px 10px;
            border-radius: 5px;
            opacity: 0;
            visibility: hidden;
            font-size: 14px;
            transition: all 0.3s ease;
            white-space: nowrap; /* Prevent tooltip text from wrapping */
        }
        .example-2 .icon-content:hover .tooltip {
            opacity: 1;
            visibility: visible;
            top: -35px; /* Adjust hover position */
        }
        .example-2 .icon-content a {
            position: relative;
            overflow: hidden;
            display: flex;
            justify-content: center;
            align-items: center;
            width: 50px;
            height: 50px;
            border-radius: 50%;
            color: #4d4d4d;
            background-color: #fff;
            transition: all 0.3s ease-in-out;
            box-shadow: 0 2px 5px rgba(0,0,0,0.1); /* Added subtle shadow */
        }
        .example-2 .icon-content a:hover {
            box-shadow: 3px 2px 45px 0px rgb(0 0 0 / 12%);
            color: white; /* Ensure icon color changes on hover */
        }

  .example-2 .icon-content a svg {
            position: relative;
            z-index: 1;
            width: 30px;
            height: 30px;
        }
        .example-2 .icon-content a .filled {
            position: absolute;
            top: auto;
            bottom: 0;
            left: 0;
            width: 100%;
            height: 0;
            background-color: #000; /* Default fill color */
            transition: all 0.3s ease-in-out;
        }
        .example-2 .icon-content a:hover .filled {
            height: 100%;
        }
        .example-2 .icon-content a[data-social="linkedin"] .filled,
        .example-2 .icon-content a[data-social="linkedin"] ~ .tooltip {
            background-color: #0274b3;
        }
        .example-2 .icon-content a[data-social="github"] .filled,
        .example-2 .icon-content a[data-social="github"] ~ .tooltip {
            background-color: #24262a;
        }
        .example-2 .icon-content a[data-social="instagram"] .filled,
        .example-2 .icon-content a[data-social="instagram"] ~ .tooltip {
            background: linear-gradient(
                45deg,
                #405de6,
                #5b51db,
                #b33ab4,
                #c135b4,
                #e1306c,
                #fd1f1f
            );
        }
        .example-2 .icon-content a[data-social="youtube"] .filled,
        .example-2 .icon-content a[data-social="youtube"] ~ .tooltip {
            background-color: #ff0000;
        }
        /* Responsive adjustments */
        @media (max-width: 768px) {
            h1 {
                font-size: 30px;
                letter-spacing: 3px;
            }
            .button {
                padding: 10px 15px;
                min-width: 100px;
            }
            .InputContainer { /* This class seems unused by the final HTML structure */
                height: 40px;
            }
            .input { /* This class seems unused by the final HTML structure */
                 height: 30px;
                 font-size: 12px;
            }
            .searc input[type="text"]:focus,
            .searc input[type="text"]:not(:placeholder-shown):not(:focus) {
                width: 200px; /* Smaller expanded search bar */
            }
            .product-container {
                max-height: 65vh; /* Adjust height on smaller screens */
                gap: 10px;
                padding: 10px;
            }
            .product {
                width: 150px; /* Smaller product cards */
            }
            .product h2 {
                font-size: 14px;
            }
            .product p {
                font-size: 12px;
            }
            .example-2 {
                flex-wrap: wrap; /* Allow icons to wrap on small screens */
                column-gap: 0.2rem;
            }
            .example-2 .icon-content a {
                width: 40px;
                height: 40px;
            }
            .example-2 .icon-content a svg {
                width: 25px;
                height: 25px;
            }
        }
        @media (max-width: 480px) {
            h1 {
                font-size: 24px;
                letter-spacing: 2px;
            }
            .button {
                padding: 8px 12px;
                font-size: 12px;
            }
            .searc input[type="text"] {
                font-size: 14px;
            }
            .searc input[type="text"]:focus,
            .searc input[type="text"]:not(:placeholder-shown):not(:focus) {
                width: 150px; /* Even smaller search bar */
            }
            .product-container {
                max-height: 60vh;
            }
            .product {
                width: calc(50% - 20px); /* Two products per row */
            }
            .product img {
                max-height: 100px;
            }
            .example-2 .icon-content {
                margin: 0 5px; /* Smaller margin for icons */
            }
        }
        /* Dark Mode Styles */
        body.dark-mode {
            background-color: #121212;
            color: #e0e0e0;
        }
        body.dark-mode h1 {
            color: #e0e0e0;
            text-shadow: 2px 2px 4px #00000080; /* Darker shadow for light text */
        }
        body.dark-mode .button {
            background: radial-gradient(ellipse at bottom, #444 0%, #222 45%);
            color: rgba(255, 255, 255, 0.8);
            box-shadow: inset 0 0 0 1px rgba(255, 255, 255, 0.05);
        }
        body.dark-mode .button::before {
            background: linear-gradient(
                90deg,
                rgba(100, 100, 100, 0) 0%,
                rgba(100, 100, 100, 1) 50%,
                rgb(90, 85, 85) 100%
            );
            opacity: 0.2;
        }
        body.dark-mode .button:hover {
            color: rgb(255, 255, 255, 1);
        }
        body.dark-mode .searc input[type="text"] {
            background: #2c2c2c;
            color: #e0e0e0;
            border: 3px solid #7a6ad4; /* Adjusted border color */
            box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.3),
                        0 6px 20px 0 #7a6ad480;
        }
        body.dark-mode .searc input[type="text"]::placeholder {
            color: #bbb;
        }
        body.dark-mode .searc input[type="text"]:focus,
        body.dark-mode .searc input[type="text"]:not(:placeholder-shown):not(:focus) {
             box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.3),
                         0 6px 20px 0 #D4A858; /* Adjusted focus shadow */
        }
        body.dark-mode .searc input[type="text"]:hover {
            box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.3),
                        0 6px 20px 0 #b396d7; /* Adjusted hover shadow */
        }
        body.dark-mode .product {
            background-color: #1e1e1e;
            border: 1px solid #444;
            color: #e0e0e0;
        }
        body.dark-mode .product h2 {
            color: #c0c0c0;
        }
        body.dark-mode .product p {
            color: #a0a0a0;
        }
        body.dark-mode .example-2 .icon-content a {
            background-color: #2c2c2c;
            color: #c0c0c0;
            box-shadow: 0 2px 5px rgba(0,0,0,0.3);
        }
        body.dark-mode .example-2 .icon-content a:hover {
            color: white;
            box-shadow: 3px 2px 45px 0px rgba(0, 0, 0, 0.2);
        }
        /* For filled icons, if they primarily use the .filled class for background */
        body.dark-mode .example-2 .icon-content a .filled {
            /* If the original fill is light, you might not need to change it, 
               but if it's dark or needs adjustment for contrast: */
            /* Example: background-color: #333; */
        }
        body.dark-mode .example-2 .icon-content .tooltip {
            background-color: #333; /* Darker tooltip background */
            color: #e0e0e0;
        }
        /* Ensure specific social icon fill colors are still visible or adjusted */
        body.dark-mode .example-2 .icon-content a[data-social="linkedin"] .filled,
        body.dark-mode .example-2 .icon-content a[data-social="linkedin"] ~ .tooltip {
            background-color: #0274b3; /* Keep original or slightly adjust if needed */
        }
        body.dark-mode .example-2 .icon-content a[data-social="github"] .filled,
        body.dark-mode .example-2 .icon-content a[data-social="github"] ~ .tooltip {
            background-color: #1A1C1E; /* Slightly darker for dark mode */
        }
        body.dark-mode .example-2 .icon-content a[data-social="github"]:hover {
            color: white; /* Ensure icon itself is white on hover */
        }
         body.dark-mode .example-2 .icon-content a[data-social="github"] svg {
            color: #e0e0e0; /* Initial icon color */
        }
        body.dark-mode .example-2 .icon-content a[data-social="github"]:hover svg {
            color: white; /* Icon color on hover */
        }
        body.dark-mode .example-2 .icon-content a[data-social="instagram"] .filled,
        body.dark-mode .example-2 .icon-content a[data-social="instagram"] ~ .tooltip {
             /* Instagram gradient usually looks good on dark, but can be adjusted if needed */
        }
        body.dark-mode .example-2 .icon-content a[data-social="youtube"] .filled,
        body.dark-mode .example-2 .icon-content a[data-social="youtube"] ~ .tooltip {
            background-color: #ff0000; /* Keep original or slightly adjust */
        }
        /* Modal Styles */
        .modal {
            display: none; /* Hidden by default */
            position: fixed; /* Stay in place */
            z-index: 1000; /* Sit on top */
            left: 0;
            top: 0;
            width: 100%; /* Full width */
            height: 100%; /* Full height */
            overflow: auto; /* Enable scroll if needed */
            background-color: rgba(0,0,0,0.4); /* Black w/ opacity */
            padding-top: 60px;
        }
        .modal-content {
            background-color: #fefefe;
            margin: 5% auto; /* 5% from the top and centered */
            padding: 20px;
            border: 1px solid #888;
            width: 80%; /* Could be more or less, depending on screen size */
            max-width: 500px; /* Maximum width */
            border-radius: 10px;
            text-align: center;
            position: relative;
        }
        .close-button {
            color: #aaa;
            position: absolute;
            top: 10px;
            right: 20px;
            font-size: 28px;
            font-weight: bold;
        }
        .close-button:hover,
        .close-button:focus {
            color: black;
            text-decoration: none;
            cursor: pointer;
        }
        /* Dark Mode Modal Styles */
        body.dark-mode .modal-content {
            background-color: #2c2c2c;
            border-color: #555;
            color: #e0e0e0;
        }
        body.dark-mode .close-button {
            color: #ccc;
        }
        body.dark-mode .close-button:hover,
        body.dark-mode .close-button:focus {
            color: #fff;
        }
        body.dark-mode #modalWhatsAppLink {
            background: radial-gradient(ellipse at bottom, #555 0%, #333 45%);
        }
    </style>
</head>
<body>
    <div style="text-align: right; width: 100%; padding: 10px; display: flex; justify-content: flex-end; align-items: center; gap: 10px;">
        <button class="button" id="darkModeToggle">🌙 Dark Mode</button>
        <button class="button">Sign Up</button>
    </div>
    <br>
    <div style="text-align: center;">
        <img src="bau.png" alt="Site Logo" width="100"> <!-- Adjusted size, ensure bau.png exists -->
    </div>
    <div style="text-align: center;">
        <h1>liquid.vape</h1>
    </div>
    <br>
    <div class="searc">
        <input type="text" placeholder="search 🔍" required>
    </div>
    <br>
    <div class="product-container">
        <div class="product" data-name="Vape 1" data-image="1.png" data-price="$19.99" style="cursor: pointer;">
            <h2>vape 1</h2>
            <img src="1.png" alt="Vape 1">
            <p>Precio: $19.99</p>
        </div>
        <div class="product" data-name="Vape 2" data-image="2.png" data-price="$24.99" style="cursor: pointer;">
            <h2>vape2</h2>
            <img src="2.png" alt="Vape 2">
            <p>Precio: $24.99</p>
        </div>
        <div class="product" data-name="Vape 3" data-image="4.png" data-price="$29.99" style="cursor: pointer;">
            <h2>vape3</h2>
            <img src="4.png" alt="Vape 3">
            <p>Precio: $29.99</p>
        </div>
        <div class="product" data-name="Vape 4" data-image="5.png" data-price="$22.50" style="cursor: pointer;">
            <h2>vape4</h2>
            <img src="5.png" alt="Vape 4">
            <p>Precio: $22.50</p>
        </div>
        <div class="product" data-name="Vape 5" data-image="6.webp" data-price="$35.00" style="cursor: pointer;">
            <h2>vape5</h2>
            <img src="6.webp" alt="Vape 5">
            <p>Precio: $35.00</p>
        </div>
        <div class="product" data-name="Vape 6" data-image="7.png" data-price="$18.75" style="cursor: pointer;">
            <h2>vape6</h2>
            <img src="7.png" alt="Vape 6">
            <p>Precio: $18.75</p>
        </div>
        <div class="product" data-name="Vape 7" data-image="8.png" data-price="$40.20" style="cursor: pointer;">
            <h2>vape7</h2>
            <img src="8.png" alt="Vape 7">
            <p>Precio: $40.20</p>
        </div>
        <div class="product" data-name="Vape 8" data-image="9.png" data-price="$33.00" style="cursor: pointer;">
            <h2>vape8</h2>
            <img src="9.png" alt="Vape 8">
            <p>Precio: $33.00</p>
        </div>
        <div class="product" data-name="Vape 9" data-image="9.png" data-price="$27.99" style="cursor: pointer;">
            <h2>vape9</h2>
            <img src="9.png" alt="Vape 9">
            <p>Precio: $27.99</p>
        </div>
    </div>
    <ul class="example-2">
        <li class="icon-content">
            <a data-social="instagram" aria-label="Instagram" href="https://www.instagram.com/liquid.vapecba/">
                <div class="filled"></div>
                <svg xml:space="preserve" viewBox="0 0 16 16" class="bi bi-instagram" fill="currentColor" height="16" width="16" xmlns="http://www.w3.org/2000/svg">
                    <path fill="currentColor" d="M8 0C5.829 0 5.556.01 4.703.048 3.85.088 3.269.222 2.76.42a3.9 3.9 0 0 0-1.417.923A3.9 3.9 0 0 0 .42 2.76C.222 3.268.087 3.85.048 4.7.01 5.555 0 5.827 0 8.001c0 2.172.01 2.444.048 3.297.04.852.174 1.433.372 1.942.205.526.478.972.923 1.417.444.445.89.719 1.416.923.51.198 1.09.333 1.942.372C5.555 15.99 5.827 16 8 16s2.444-.01 3.298-.048c.851-.04 1.434-.174 1.943-.372a3.9 3.9 0 0 0 1.416-.923c.445-.445.718-.891.923-1.417.197-.509.332-1.09.372-1.942C15.99 10.445 16 10.173 16 8s-.01-2.445-.048-3.299c-.04-.851-.175-1.433-.372-1.941a3.9 3.9 0 0 0-.923-1.417A3.9 3.9 0 0 0 13.24.42c-.51-.198-1.092-.333-1.943-.372C10.443.01 10.172 0 7.998 0zm-.717 1.442h.718c2.136 0 2.389.007 3.232.046.78.035 1.204.166 1.486.275.373.145.64.319.92.599s.453.546.598.92c.11.281.24.705.275 1.485.039.843.047 1.096.047 3.231s-.008 2.389-.047 3.232c-.035.78-.166 1.203-.275 1.485a2.5 2.5 0 0 1-.599.919c-.28.28-.546.453-.92.598-.28.11-.704.24-1.485.276-.843.038-1.096.047-3.232.047s-2.39-.009-3.233-.047c-.78-.036-1.203-.166-1.485-.276a2.5 2.5 0 0 1-.92-.598 2.5 2.5 0 0 1-.6-.92c-.109-.281-.24-.705-.275-1.485-.038-.843-.046-1.096-.046-3.233s.008-2.388.046-3.231c.036-.78.166-1.204.276-1.486.145-.373.319-.64.599-.92s.546-.453.92-.598c.282-.11.705-.24 1.485-.276.738-.034 1.024-.044 2.515-.045zm4.988 1.328a.96.96 0 1 0 0 1.92.96.96 0 0 0 0-1.92m-4.27 1.122a4.109 4.109 0 1 0 0 8.217 4.109 4.109 0 0 0 0-8.217m0 1.441a2.667 2.667 0 1 1 0 5.334 2.667 2.667 0 0 1 0-5.334"></path>
                </svg>
            </a>
            <div class="tooltip">Instagram</div>
        </li>
 <!-- Add other social media icons here if needed, example:
  <li class="icon-content">
 <a data-social="github" aria-label="Github" href="#">
 <div class="filled"></div>
 <svg>...</svg>
</a>
    <div class="tooltip">Github</div>
 </li>
-->
    </ul>
    <!-- The Modal -->
    <div id="productModal" class="modal">
        <div class="modal-content">
            <span class="close-button">&times;</span>
            <img id="modalImage" src="" alt="Product Image" style="width: 100%; max-width: 300px; height: auto; border-radius: 5px; margin-bottom: 15px;">
            <h2 id="modalName">Product Name</h2>
            <p id="modalPrice">Price: $0.00</p>
            <!-- <p id="modalDescription">Some description here...</p> -->
            <a id="modalWhatsAppLink" href="#" target="_blank" class="button" style="margin-top: 10px; display: inline-block;">Contact on WhatsApp</a>
        </div>
    </div>
    <script>
        // Dark Mode Toggle
        const darkModeToggle = document.getElementById('darkModeToggle');
        const body = document.body;
        if (localStorage.getItem('darkMode') === 'enabled') {
            body.classList.add('dark-mode');
            darkModeToggle.textContent = '☀️ Light Mode';
        }
        darkModeToggle.addEventListener('click', () => {
            body.classList.toggle('dark-mode');
            if (body.classList.contains('dark-mode')) {
                localStorage.setItem('darkMode', 'enabled');
                darkModeToggle.textContent = '☀️ Light Mode';
            } else {
                localStorage.setItem('darkMode', 'disabled');
                darkModeToggle.textContent = '🌙 Dark Mode';
            }
        });
        // Modal Logic
        const modal = document.getElementById('productModal');
        const modalName = document.getElementById('modalName');
        const modalImage = document.getElementById('modalImage');
        const modalPrice = document.getElementById('modalPrice');
        const modalWhatsAppLink = document.getElementById('modalWhatsAppLink');
        const closeButton = document.querySelector('.close-button');
    const products = document.querySelectorAll('.product');
        products.forEach(product => {
            product.addEventListener('click', () => {
                const name = product.dataset.name;
                const image = product.dataset.image;
                const price = product.dataset.price;
                const whatsappNumber = "+5493544486036"; // Placeholder WhatsApp number
                modalName.textContent = name;
                modalImage.src = image;
                modalImage.alt = name; // Set alt text for accessibility
                modalPrice.textContent = `Precio: ${price}`;
                const message = `Hola, estoy interesado/a en el producto: ${name} - Precio: ${price}`;
                modalWhatsAppLink.href = `https://wa.me/${whatsappNumber}?text=${encodeURIComponent(message)}`;              
                modal.style.display = 'block';
            });
        });
        closeButton.addEventListener('click', () => {
            modal.style.display = 'none';
        });
        // Close modal if user clicks outside of the modal content
        window.addEventListener('click', (event) => {
            if (event.target === modal) {
                modal.style.display = 'none';
            }
        });

    </script>
</body>
</html>

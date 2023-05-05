Download Link: https://assignmentchef.com/product/solved-cse241-homework-2
<br>
<h1>Image Editor</h1>

<ul>

 <li>You can create a class which represents the whole image editor program. Your program won’t have a GUI yet and you need to do is decide how to organize events and data in your program.</li>

 <li>Implement a menu system.</li>

 <li>Implement member functions for reading image files and writing image data to files.</li>

 <li>Currently, your image editor program opens only one image and operates on it. Later, you will extend your program to open more than one image at a time.</li>

 <li>Implement grayscale conversion function.</li>

</ul>

<h1>Image File Format</h1>

Your program will basically work on PPM format(Ascii format). Particularly P3 format. Read the description here: <a href="https://www.cs.swarthmore.edu/~soni/cs35/f13/Labs/extras/01/ppm_info.html">http://netpbm.sourceforge.net/doc/ppm.html</a>

Many image editors can read and write ppm files. I advise you to use <sub>GIMP</sub>. Use <sub>Ascii </sub>format while exporting, otherwise you cannot read it.

<h1>Menu Of Your Program</h1>

The initial version of your program will have the following main menu structure:

Main Menu

<table width="676">

 <tbody>

  <tr>

   <td width="188">0 – Exit</td>

   <td width="488">—–&gt; Exits the program without saving the image data</td>

  </tr>

  <tr>

   <td width="188">1 – Open An Image(D)</td>

   <td width="488">—–&gt; A dialog entity in order for user to enter a file name.</td>

  </tr>

  <tr>

   <td width="188">2 – Save Image Data(D)</td>

   <td width="488">—–&gt; A dialog entity for saving the current state of the image data.</td>

  </tr>

  <tr>

   <td width="188">3 – Scripts(D)</td>

   <td width="488">—–&gt; Various scripts</td>

  </tr>

 </tbody>

</table>

OPEN AN IMAGE MENU

<ul>

 <li>– UP</li>

 <li>– Enter The Name Of The Image File</li>

</ul>

SAVE IMAGE DATA MENU

<ul>

 <li>– UP</li>

 <li>– Enter A File Name</li>

</ul>

SCRIPTS MENU

<ul>

 <li>– UP</li>

 <li>– Convert To Grayscale(D)</li>

</ul>

CONVERT TO GRAYSCALE MENU

<ul>

 <li>– UP</li>

 <li>– Enter Coefficients For RED GREEN And BLUE Channels.</li>

</ul>

If a menu item has a <sub>(D) </sub>at the end, that means it is a dialog. If user enter the particular menu number, A new menu dialog will be shown.

<strong>Example</strong>

Suppose that you have the following file.

<ul>

 <li>test.ppm</li>

</ul>

<table width="335">

 <tbody>

  <tr>

   <td width="70">P34 4255</td>

   <td width="105"> </td>

   <td width="77"> </td>

   <td width="42"> </td>

   <td width="42"> </td>

  </tr>

  <tr>

   <td width="70">0 0 0</td>

   <td width="105">100 0 0</td>

   <td width="77">0 0 0</td>

   <td width="42">255</td>

   <td width="42">0 255</td>

  </tr>

  <tr>

   <td width="70">0 0 0</td>

   <td width="105">0 255 175</td>

   <td width="77">0 0 0</td>

   <td width="42">0</td>

   <td width="42">0 0</td>

  </tr>

  <tr>

   <td width="70">0 0 0</td>

   <td width="105">0 0 0</td>

   <td width="77">0 15 175</td>

   <td width="42">0</td>

   <td width="42">0 0</td>

  </tr>

  <tr>

   <td colspan="2" width="174">255 0 255 0 0 0</td>

   <td width="77">0 0 0</td>

   <td colspan="2" width="84">255 255 255</td>

  </tr>

 </tbody>

</table>

<strong>NOTE</strong>: <sub>&gt; </sub>is a part of the terminal environment. <strong>DO NOT PRINT IT</strong>

Start your program

&gt; ./myprogram

&gt; MAIN MENU

&gt; 0 – Exit

&gt; 1 – Open An Image(D)

&gt; 2 – Save Image Data(D)

&gt; 3 – Scripts(D)

&gt; 1                                                                            ——–&gt; User inputs 1 and presses RETURN

&gt; OPEN AN IMAGE MENU

&gt; 0 – UP                                                                        ——–&gt; If user enters 0, MAIN MENU will be printed.

&gt; 1 – Enter The Name Of The Image File

&gt; 1                                                                            ——–&gt; User inputs 1 and presses RETURN

&gt; test.ppm                                                               ——–&gt; User inputs test.ppm and presses RETURN

&gt; OPEN AN IMAGE MENU   ——–&gt; Your program reads test.ppm and prints the current dialog menu &gt; 0 – UP              ——–&gt; If user enters 0, MAIN MENU will be printed.

&gt; 1 – Enter The Name Of The Image File

&gt; 0                                                                            ——–&gt; User inputs 0 and presses RETURN

&gt; MAIN MENU                                                     ——–&gt; MAIN MENU is printed again

&gt; 0 – Exit

&gt; 1 – Open An Image(D)

&gt; 2 – Save Image Data(D)

&gt; 3 – Scripts(D) .

.

.

<h1>Script: Convert To Grayscale</h1>

This script creates the following dialog:

CONVERT TO GRAYSCALE MENU

<ul>

 <li>– UP</li>

 <li>– Enter Coefficients For RED GREEN And BLUE Channels.</li>

</ul>

If user enters <sub>1</sub>, then user can enter three float numbers which are in the range [0,1). You should check for any errors. Example input:

0.33 0.10 0.2

These numbers are coefficients (<sub>c_r</sub>, <sub>c_g</sub>, <sub>c_b</sub>) for <sub>RED</sub>, <sub>GREEN </sub>and <sub>BLUE </sub>channels. After getting the coefficients (<sub>c_r</sub>, c_g, <sub>c_b</sub>) you can convert each color to grayscale using the following formula:

RED = (c_r * RED) + (c_g * GREEN) + (c_b * BLUE)

GREEN = (c_r * RED) + (c_g * GREEN) + (c_b * BLUE) BLUE = (c_r * RED) + (c_g * GREEN) + (c_b * BLUE)

You just need to update the values in the image representation these new values. If the new values are greater than 255, then that means they are saturated. Leave them as <sub>255</sub>.

<h1>Saving Image Data</h1>

SAVE IMAGE DATA MENU

<ul>

 <li>– UP</li>

 <li>– Enter A File Name</li>

</ul>

If user enters <sub>1</sub>, then user can enter a filename. Assume user enters <sub>output.ppm</sub>. In this case, image data in the memory will be saved as <sub>output.ppm</sub>.

<h1>Remarks</h1>

<ul>

 <li>Error checking is important.</li>

 <li>Your program should be immune to the whitespace before any user input.</li>

 <li>Do not submit your code without testing it with several different scenarios.</li>

 <li>Write comments in your code. Extensive commenting is required. Comment on every variable, constant, function and loop. (<sub>10pts</sub>)</li>

 <li>Do not use <sub>#Define </sub>and define macros. Instead use <sub>constant </sub>keyword and define constant variables. If you use macros, you will loose <sub>5 </sub>points for each of them.</li>

 <li>Everything happens through <sub>stdin </sub>and <sub>stdout</sub>.</li>

 <li>Be very careful about the input and output format. Don’t print anything extra(including spaces).</li>

 <li>You have to use <sub>Class</sub>. You should use inheritance and other advanced OOP mechanisms yet.</li>

 <li>You can use std::string and std::vector.</li>

</ul>

<strong>Turn in:</strong>

<ul>

 <li>Source code of a complete C++ program. Name of the file should be in this format: <sub>&lt;full_name&gt;_&lt;id&gt;.cpp</sub>. If you do not follow this naming convention you will loose <sub>-10 </sub></li>

 <li>Example: <sub>cpp</sub>. Please do not use any Turkish special characters.</li>

 <li>You don’t need to use an IDE for this assignment. Your code will be compiled and run in a command window.</li>

 <li>Your code will be compiled and tested on a Linux machine(Ubuntu). GCC will be used.</li>

 <li>Make sure you don’t get compile errors when you issue this command : <sub>g++ -std=c++11 &lt;full_name&gt;_&lt;id&gt;.cpp</sub>.</li>

 <li>A script will be used in order to check the correctness of your results. So, be careful not to violate the expected output format.</li>

 <li>Provide comments unless you are not interested in partial credit. (If I cannot easily understand your design, you may loose points.)</li>

</ul>
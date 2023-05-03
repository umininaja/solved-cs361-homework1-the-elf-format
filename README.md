Download Link: https://assignmentchef.com/product/solved-cs361-homework1-the-elf-format
<br>
The primary objective of this homework is to get you familiarized with the ELF file format and the process of linking executables. The secondary goal of this assignment is to give you some experience using the Gradescope autograder and turnin system.

We covered using git in the first lab, but if you’re still not that familiar with it, this assignment is a second chance to get up to speed. Remember: git gives you warnings and errors <em>for good reason</em>, if it complains at the command line when you run a command, don’t just assume it’s completed correctly!

Setting git to the simple push is a helpful quality of life improvement, this is recommended but not required:

git config –global push.default simple

You should also tell git who you are, otherwise it will complain that you are some anonymous coder. Do this, but use your own name and email. Note that if you do not change your username and email properly, you won’t get credit.

$ git config –global user.name “Copypasting Carol”

$ git config –global user.email <u>cop</u>y<u>pasta</u>@<u>domain.invalid</u>

Th<span style="text-decoration: line-through;"><u>e</u></span> skeleton code for this assignment is available at <a href="https://www.google.com/url?q=https%3A%2F%2Fclassroom.github.com%2Fa%2FVl5AyoXH&amp;sa=D&amp;sntz=1&amp;usg=AFQjCNE6HOckhf09lHWkOwFD7Ftya65Uvg">this link</a><a href="https://www.google.com/url?q=https%3A%2F%2Fclassroom.github.com%2Fa%2FVl5AyoXH&amp;sa=D&amp;sntz=1&amp;usg=AFQjCNE6HOckhf09lHWkOwFD7Ftya65Uvg">.</a> You must use GitHub classroom to manage your code (the repository created through that link). You will need to su<a href="https://sites.google.com/uic.edu/cs361summer2020/home?authuser=1">bmit the code via Gradescope</a><a href="https://sites.google.com/uic.edu/cs361summer2020/home?authuser=1">.</a>

<a href="https://sites.google.com/uic.edu/cs361summer2020/home?authuser=1">CS 361 Summer 2020</a>                            <a href="https://sites.google.com/uic.edu/cs361summer2020/home?authuser=1">Home</a>         <a href="https://sites.google.com/uic.edu/cs361summer2020/schedule?authuser=1">Schedule</a>         <a href="https://sites.google.com/uic.edu/cs361summer2020/homeworks?authuser=1">Homeworks</a>

No<a href="https://sites.google.com/uic.edu/cs361summer2020/home?authuser=1">w that you have the skeleton code</a>, you can start coding. You should commit early and often, and push to your remote repository whenever is convenient to back up your work!

<h2>Programming environment</h2>

This assignment was created in a Debian-derived Linux environment. This assignment is simple enough that any Linux environment with an up to date gcc will be sufficient, including systems1.cs.uic.edu. The autograder is written to the correct specification for the autograding environment. Feel free to complete this on a lab machine, a local Linux VM, or elsewhere.

<strong>The Programming Part!</strong>

This part will give you a quick introduction to using readelf to better understand the linking process.

In this assignment, you must fill hw1.c and hw1.h with code which will:

<ol>

 <li>cause your UIC netID (and nothing else) to be printed on the first line of output when the program is run.</li>

 <li>cause gcc -Wall hw1.c to issue zero warnings and zero errors.</li>

 <li>cause the output of readelf -s hw1.o to have an identical number of symbol table entries as shown below (25 entries).</li>

 <li>cause the output of readelf -s hw1.o to have identical values in the bold sections of the output below:</li>

</ol>

You can perform the symbol table check by running make test within the hw1 directory. A full credit solution will have output that looks like:

Symbol table ‘.symtab’ contains 25 entries:

Num: Value            Size Type     Bind   Vis     Ndx Name

0:   0000000000000000 0    NOTYPE   LOCAL  DEFAULT UND

1:   0000000000000000 0    FILE     LOCAL  DEFAULT ABS hw1.c

2:   0000000000000000 0    SECTION  LOCAL  DEFAULT 1

3:   0000000000000000 0    SECTION  LOCAL  DEFAULT 3

4:   0000000000000000 0    SECTION  LOCAL  DEFAULT 4

5:   0000000000000000 11   <strong>FUNC</strong>     <strong>LOCAL</strong>  DEFAULT <strong>1</strong>   <strong>I_have_written</strong>

6:   0000000000000000 <strong>12</strong>   <strong>OBJECT</strong>   <strong>LOCAL</strong>  DEFAULT <strong>3</strong>   <strong>the_code</strong>

7: 000000000000000b 26 <strong>FUNC LOCAL </strong>DEFAULT <strong>1 that you needed </strong>7:   000000000000000b 26   <strong>FUNC</strong>     <strong>LOCAL</strong>  DEFAULT <strong>1</strong>   <strong>that_you_needed</strong>

<u>8</u><a href="https://sites.google.com/uic.edu/cs361summer2020/home?authuser=1">:   0000000000000018 </a><a href="https://sites.google.com/uic.edu/cs361summer2020/home?authuser=1"><strong>4</strong></a><a href="https://sites.google.com/uic.edu/cs361summer2020/home?authuser=1">    </a><a href="https://sites.google.com/uic.edu/cs361summer2020/home?authuser=1"><strong>O</strong></a><strong>BJECT</strong>   <strong>L</strong><a href="https://sites.google.com/uic.edu/cs361summer2020/home?authuser=1"><strong>OCAL</strong></a>  D<a href="https://sites.google.com/uic.edu/cs361summer2020/schedule?authuser=1">EFAULT </a><a href="https://sites.google.com/uic.edu/cs361summer2020/schedule?authuser=1"><strong>3</strong></a>   <a href="https://sites.google.com/uic.edu/cs361summer2020/homeworks?authuser=1"><strong>to_compil</strong></a><strong>e</strong>.2213

<a href="https://sites.google.com/uic.edu/cs361summer2020/home?authuser=1">CS 361 Summer 2020</a>                            <a href="https://sites.google.com/uic.edu/cs361summer2020/home?authuser=1">Home</a>         <a href="https://sites.google.com/uic.edu/cs361summer2020/schedule?authuser=1">Schedule</a>         <a href="https://sites.google.com/uic.edu/cs361summer2020/homeworks?authuser=1">Homeworks</a>

9<a href="https://sites.google.com/uic.edu/cs361summer2020/home?authuser=1">:   0000000000000000 0    S</a>ECTION  LOCAL  DEFAULT 5

10:  0000000000000058 78   <strong>FUNC</strong>     <strong>LOCAL</strong>  DEFAULT <strong>1</strong>   <strong>and_which</strong>

11:  000000000000001c <strong>4</strong>    <strong>OBJECT</strong>   <strong>LOCAL</strong>  DEFAULT <strong>3</strong>

<strong>has_a_bunch_of</strong>.2220

12:  0000000000000020 <strong>4</strong>    <strong>OBJECT</strong>   <strong>LOCAL</strong>  DEFAULT <strong>3</strong>   <strong>ridiculous</strong>.2221 13:  0000000000000000 <strong>8</strong>    <strong>OBJECT</strong>   <strong>LOCAL</strong>  DEFAULT <strong>4</strong>   <strong>symbols</strong>.2222

14:  0000000000000000 0    SECTION  LOCAL  DEFAULT 7

15:  0000000000000000 0    SECTION  LOCAL  DEFAULT 8

16:  0000000000000000 0    SECTION  LOCAL  DEFAULT 6

17:  0000000000000000 7    <strong>FUNC</strong>     <strong>GLOBAL</strong> DEFAULT <strong>1</strong>   <strong>sides_and</strong>

18:  0000000000000025 61   <strong>FUNC</strong>     <strong>GLOBAL</strong> DEFAULT <strong>1</strong>   <strong>main</strong>

19:  0000000000000000 <strong>0</strong>    <strong>NOTYPE</strong>   <strong>GLOBAL</strong> DEFAULT <strong>UND</strong>

<strong>__GLOBAL__OFFSET__TABLE__</strong>

20:  0000000000000000 <strong>0</strong>    <strong>NOTYPE</strong>   <strong>GLOBAL</strong> DEFAULT <strong>UND</strong> <strong>printf</strong>

21:  00000000000000a6 47   <strong>FUNC</strong>     <strong>GLOBAL</strong> DEFAULT <strong>1</strong>   <strong>Forgive_me</strong>

22:  0000000000000004 <strong>4</strong>    <strong>OBJECT</strong>   <strong>GLOBAL</strong> DEFAULT <strong>COM</strong> <strong>they_are_arbitrary</strong>

23:  0000000000000010 <strong>8</strong>    <strong>OBJECT</strong>   <strong>GLOBAL</strong> DEFAULT <strong>3</strong>   <strong>so_random</strong>

24:  00000000000000d5 41   <strong>FUNC</strong>     <strong>GLOBAL</strong> DEFAULT <strong>1</strong>   <strong>and_so_varied</strong>

Hints:

Are you seeing puts instead of printf? Check the man pages for what the difference is, and make sure that the compiler can’t optimize away your call to printf. Remember, requirement #1 <strong>only</strong> mentions the <strong>first</strong> line of output.

The four digit numbers do not need to made identical, but you do need to make them show up. Keep experimenting with different variable types until you find how to create variables with periods and numbers on them.

Function lengths are very difficult to reproduce – note that for every FUNC, you do not have to duplicate the length (the length is the number of bytes of assembly code chosen by the compiler to execute the body of each function).
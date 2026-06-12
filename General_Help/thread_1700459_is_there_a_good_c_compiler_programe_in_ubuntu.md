---
title: "is there a good c compiler programe in ubuntu"
date: 2011-03-05
forum: General Help
---

### Post by jolian ramos on 2011-03-05
is there a good c compiler programe in ubuntu

---

### Post by rishabhpadita on 2011-03-05
Gcc is the Best.
And try coding in terminal it's gr8

---

### Post by jolian ramos on 2011-03-05
> **rishabhpadita said:**
> Gcc is the Best.
And try coding in terminal it's gr8
is Gcc a good alternative like borland c++ compiler in microsoft windows ?

---

### Post by lykeion on 2011-03-05
Gnu Compiler Collection (gcc)

Homepage: [http://gcc.gnu.org/](http://gcc.gnu.org/)
Wikipedia: [http://en.wikipedia.org/wiki/GNU_Compiler_Collection](http://en.wikipedia.org/wiki/GNU_Compiler_Collection)

Ubuntu forums threads:
[Programming Tools and References]("http://ubuntuforums.org/showthread.php?t=1006662") 
[How to start programming - guides and links for many languages]("http://ubuntuforums.org/showthread.php?t=333867")

Install:
```
sudo apt-get install gcc
```

---

### Post by jolian ramos on 2011-03-05
> **lykeion said:**
> Gnu Compiler Collection (gcc)

Homepage: [http://gcc.gnu.org/](http://gcc.gnu.org/)
Wikipedia: [http://en.wikipedia.org/wiki/GNU_Compiler_Collection](http://en.wikipedia.org/wiki/GNU_Compiler_Collection)

Ubuntu forums threads:
[Programming Tools and References]("http://ubuntuforums.org/showthread.php?t=1006662") 
[How to start programming - guides and links for many languages]("http://ubuntuforums.org/showthread.php?t=333867")

Install:
```
sudo apt-get install gcc
```
ok i install it using sudo apt-get install gcc but i can't find the installed programe in the menu of application 

how to open it  !!!!!!!!!!

---

### Post by WorMzy on 2011-03-05
You don't open it, you point it at the source code you want to compile, and it compiles it.

I think what you're looking for is an integrated development environment (IDE). Here's a nice long list for you to look at: [http://linuxmafia.com/faq/Devtools/ides.html](http://linuxmafia.com/faq/Devtools/ides.html)

---

### Post by jolian ramos on 2011-03-05
> **WorMzy said:**
> You don't open it, you point it at the source code you want to compile, and it compiles it.

I think what you're looking for is an integrated development environment (IDE). Here's a nice long list for you to look at: [http://linuxmafia.com/faq/Devtools/ides.html](http://linuxmafia.com/faq/Devtools/ides.html)

all  what i want is program like borland c++ compiler in microsoft windows to open it  something like matlab where you can open file and write inside it then run or debug your code which you wrote

i don't know how to use your list that you gave me 
by the way i am not expert at all in ubuntu , i use it since just few days ,so please detail your post as you can to be able to understand you 
thank you

---

### Post by jolian ramos on 2011-03-05
for example i click on the first link in the list you gave me as it contain many thing c c++ html etc.....

General/Editors:          
[LIST=1]
[*][Amy]("http://sunsite.dk/amy/") (HTML, C,           C++, Java, SQL, LaTeX, Makefiles and many more           languages)
[/LIST]
but the link gave me "page not found "

so i want that programe so what should i do , i google for Amy but there was no IDE called Amy

---

### Post by debd on 2011-03-05
open software center , search for "geany"
install it . its the best one i've seen so far.
u may have to build up ur header files library coz  I Didn't find some common header files in the include folder. just surf the system category in the soft center. u'll find lots of c++ enhancement  packages. those  mainly adds different headers in the library.

---

### Post by wiggly81 on 2011-03-05
a quick search in the Ubuntu Software Center for "C++" gave these among other results..
Code::Blocks
Anjuta
CodeLite

---

### Post by stjohnmedrano on 2011-03-05
try geany, very light, you can even write your csharps code

---

### Post by jolian ramos on 2011-03-05
i download the anjuta from its site then i open install file to read it and get instruction of installation 

the first step was done with no problem but the other steps give errors 
this is picture for instructions ,error in terminal and the contains of the extracted folder after dowloaded it from anjuta . Hope that you can tell me where is the problem in hindering installation 



[IMG]http://img96.imageshack.us/img96/7564/screenshotjie.png[/IMG]

---

### Post by vivek.pandey on 2011-03-05
you are thinking of writing codes in c or c++?

---

### Post by jolian ramos on 2011-03-05
> **neo_aryan said:**
> you are thinking of writing codes in c or c++?
yes sir i hope you can help me in installing anjuta from the file which i already download from its site which i provide pictures for it in the same previous post of me

---

### Post by vivek.pandey on 2011-03-05
well i cant help yoou in installing that but i would suggest an easier way to write, compile and run codes . for c++
download g++ compiler
how can you dowload it?
on terminal type g++
you will get a list of available packages chose any and install sudo apt-get install package name
next write any code in c++ in a text editor save it as .cpp or .c++
compilation
on terminal type this
g++ filename here filename is the name of the file
if no errors then run as ./a.out   on terminal
you will get the output dont think since you need terminal it would be difficult . it is damn easy.. if you need any assisstance in this i am there for help any time..

---


---
title: "complete noob:  Running a program (not from package manager)"
date: 2010-12-23
forum: General Help
---

### Post by ubuu on 2010-12-23
Hi everyone, I am new to Ubuntu, I'd really appreciate it if someone could help get a certain program working


I downloaded this and extracted this to my home folder:

[http://download.cnet.com/KaKs-Calculator/3000-2383_4-75305712.html](http://download.cnet.com/KaKs-Calculator/3000-2383_4-75305712.html)

- typed in KaKs_Calculator, it said "command not found"
- went to folder:  KaKs_Calculator2.0/bin/Linux...typed in ./KaKs_Calculator, it said "permission denied"
- changed permission by typing chmod ugo+x KaKs_Calculator
- now typed in ./KaKs_Calculator...it says "cannot execute binary file"

I'm getting lost here can someone help me out?

---

### Post by hhh on 2010-12-23
From your link...
> Operating system: Windows 98/Me/2000/XP/Vista/7/NT

---

### Post by Frogs Hair on 2010-12-23
Hi and Welcome

That is a Windows program , so you won't be able to use it unless you run it in wine.
[http://www.psychocats.net/ubuntu/wine](http://www.psychocats.net/ubuntu/wine)

---

### Post by hhh on 2010-12-23
I did a little more digging, and this program is supposed to run on Linux...
[http://sourceforge.net/projects/kakscalculator2/](http://sourceforge.net/projects/kakscalculator2/)
The manual.pdf says to switch to the src directory and run make, which I did. I also set KaKs_Calculator in the /bin/Linux folder to executable as you did. I couldn't get it to run.

---

### Post by ubuu on 2010-12-23
whoa 3 replies already haha cool :grin:

yeah its supposed to run on Linux...the documentation included linux commands...

---

### Post by ubuu on 2010-12-23
From the manual:  

[B]2.2.1 Linux/Unix
KaKs_Calculator 2.0 has been tested on ROCKS LINUX 4.3 X86-64 platform.
.
&#9679;Unpack the package of KaKs_CalculatorXXX.tar.gz by the following commands.

gzip –d KaKs_CalculatorXXX.tar.gz
tar –xf KaKs_CalculatorXXX.tar

&#9679;If you use other Linux/Unix OS, you have to compile the program in the source codes folder with the help of g++/gcc compiler by yourselves.

cd KaKs_CalculatorXXX/src
make
[/B]
so is it possible that it only works on that "Rocks Linux 4.3" ?  

If so, I guess I could try finding/installing that version of Linux (I want to use this program that badly)....

---

### Post by ridetheteapot on 2010-12-23
ummmm, extract the package
 navigate to ./KaKs_Calculator2.0/bin/Linux/  <----see its already built you silly billies ;)

chmod +x ./Kaks_Calculator

try this example:
./KaKs_Calculator -i ../../examples/example.axt -o ~/test.axt.kaks -m GMYN

works fine for me, maybe i have dependencies installed by coincidence, i didn't look them up.
So my guess is your running 32bit?
$file ~/Downloads/KaKs_Calculator2.0/bin/Linux/KaKs_Calculator
KaKs_Calculator: ELF 64-bit LSB executable, x86-64, version 1 (SYSV), dynamically linked
prebuilt is a 64bit file. If you are running 32bits just rm -rf the package's bin folder and recompile.

---

### Post by ubuu on 2010-12-23
so I didn't get what you said, but the key I got was that it does work hahaa:D

So yeah I do have a 32-bit, can you explain again what to do again?

" just rm -rf the package's bin folder and recompile"...


I just tried deleting the bin folder in KaKs_Calculator2.0, navigated to src folder, and typed "make" and it gave a bunch of errors...so it didn't work

(BTW I have downloaded "build essential" )

---

### Post by ridetheteapot on 2010-12-23
ok here you go:

[LIST]
[*]extract the package
[*]go to ./KaKs_Calculator2.0/src
[*]grab build-essential, maybe need it for the libs and make(**sudo apt-get install build-essential**) --- nevermind that
[*]you'll have to edit 3 files **gedit KaKs.cpp base.cpp GY94.cpp** and add *#include <string.h>* just add it after the other includes.
[*]now you can run **make**
[*]the binary will be sitting there for you to use type **./KaKs_Calculator -h** for some syntax
[/LIST]

---

### Post by Spyderkid on 2010-12-23
If its a .zip file right click and do extract.

edit 3 files run```
 gedit KaKs.cpp base.cpp GY94.cpp 
```
and add #include <string.h> after include

then run make

Then run```
./KaKs_Calculator -h
``` to start the program

---

### Post by ubuu on 2010-12-23
wow thanks for the instructions guys - its not quite working but its almost there...

after editing the files, when I did "make" there was some output:  

g++  -O -o  KaKs_Calculator  KaKs_Calculator.cpp KaKs.cpp MSMA.cpp MYN.cpp base.cpp NG86.cpp LWL85.cpp LPB93.cpp GY94.cpp YN00.cpp -lstdc++ -lm
base.cpp: In member function ‘std::string Base::parseOutput()’:
base.cpp:480: warning: NULL used in arithmetic
base.cpp:480: warning: NULL used in arithmetic
base.cpp:480: warning: NULL used in arithmetic
base.cpp:491: warning: NULL used in arithmetic
base.cpp:491: warning: NULL used in arithmetic
base.cpp:491: warning: NULL used in arithmetic

does that mean anything?

right now if I go to src folder, ./KaKs_Calculator -h works

but if I try the basic example:
./KaKs_Calculator -i ../../examples/example.axt -o ~/test.axt.kaks -m GMYN

it says: 
Input parameter(s) error.

---

### Post by ridetheteapot on 2010-12-23
do this
./KaKs_Calculator -i ../examples/example.axt -o ~/test.axt.kaks -m GMYN
Mission Accomplished 0.0s

(your in a different directory now)

@Spyderkid
you just think code is prettier then list don't you

---

### Post by ubuu on 2010-12-23
ok yeah that works...I thought I tried ../ and ../.. before but I guess not 

Thanks a lot for the help guys

now I just have to actually use the software and do some work haha :D

thanks again

---

### Post by ubuu on 2010-12-24
Hey guys, just a follow up on this...If I wanted to call that program repeatedly
 
./KaKs_Calculator -i ../examples/example.axt -o ~/test.axt.kaks -m GMYN
 
for 100 different input files (and ideally keep adding output to the same output file), what would you suggest? 
 
if you can point me somewhere I can go read up on it...

---

### Post by ridetheteapot on 2010-12-24
bash scripting will do it easy, you might as well read up a little.
loops:
[http://www.cyberciti.biz/faq/bash-for-loop/](http://www.cyberciti.biz/faq/bash-for-loop/)
[http://www.cyberciti.biz/faq/bash-while-loop/](http://www.cyberciti.biz/faq/bash-while-loop/)
pipes and redirection (for consolidating the output or whatever)
[http://www.itk.ntnu.no/ansatte/Hendseth_Sverre/bash/pipes.html](http://www.itk.ntnu.no/ansatte/Hendseth_Sverre/bash/pipes.html)

theres a thousand ways to skin this cat, so just try a little, if nothing is working out i'll give you a hand. happy xmas eve - i gotta go shopping :-O

---


---
title: "LMMS installation for novice help"
date: 2011-05-19
forum: General Help
---

### Post by Minimula on 2011-05-19
Hi guys, I'm sure you get many of these types of requests from complete beginners like myself, but here goes nothing!

I'm new to Ubuntu, my original Windows Vista died on me and no longer wants to reinstall for some reason, so I got Ubuntu 11.04 on my pen drive and I am loving it so far so have fully installed it. I have a read about the terminal etc, and although it's slightly confusing, I'm slowly getting to grips with it.

Here is where my problem begins. I was looking for an alternative to FruityLoops, and discovered LMMS. I downloaded it, but for the life of me, cannot work out how to install it.

I did a search on here and found some instructions but I did not understand them fully so it failed. I have also tried using the instructions bundled in with the package to no avail. 

I get an error whilst trying to follow these steps...

mkdir build
cd build
cmake ../
make
sudo make install


Here is the error...

[I]mike@mike-Studio-1535:~/build$ cmake ../
CMake Error: The source directory "/home/mike" does not appear to contain CMakeLists.txt.
Specify --help for usage, or press the help button on the CMake GUI.[/I]

I am really not sure what to do, I have CMake installed, and I have also extracted the LMMS files into my home folder :confused:

I appreciate greatly, ANY help on this matter, i'm lost without my FruityLoops!

---

### Post by wildmanne39 on 2011-05-19
> **Minimula said:**
> Hi guys, I'm sure you get many of these types of requests from complete beginners like myself, but here goes nothing!

I'm new to Ubuntu, my original Windows Vista died on me and no longer wants to reinstall for some reason, so I got Ubuntu 11.04 on my pen drive and I am loving it so far so have fully installed it. I have a read about the terminal etc, and although it's slightly confusing, I'm slowly getting to grips with it.

Here is where my problem begins. I was looking for an alternative to FruityLoops, and discovered LMMS. I downloaded it, but for the life of me, cannot work out how to install it.

I did a search on here and found some instructions but I did not understand them fully so it failed. I have also tried using the instructions bundled in with the package to no avail. 

I get an error whilst trying to follow these steps...

mkdir build
cd build
cmake ../
make
sudo make install


Here is the error...

[I]mike@mike-Studio-1535:~/build$ cmake ../
CMake Error: The source directory "/home/mike" does not appear to contain CMakeLists.txt.
Specify --help for usage, or press the help button on the CMake GUI.[/I]

I am really not sure what to do, I have CMake installed, and I have also extracted the LMMS files into my home folder :confused:

I appreciate greatly, ANY help on this matter, i'm lost without my FruityLoops!
Hi, if that linux is hard to install try one like ubuntu that installs its almost.

---

### Post by Minimula on 2011-05-19
> **wildmanne39 said:**
> Hi, if that linux is hard to install try one like ubuntu that installs its almost.

Hi there, thanks for your reply. I'm not having any issue installing the OS, I have Ubuntu running perfectly on my laptop right now.

It's the program LMMS that I am having issues installing.

---

### Post by wildmanne39 on 2011-05-20
> **Minimula said:**
> Hi there, thanks for your reply. I'm not having any issue installing the OS, I have Ubuntu running perfectly on my laptop right now.

It's the program LMMS that I am having issues installing.
HI, of I spaced out for a minute I am helping alot of people at the same time and sometimes I fail. that program is in synaptic package manager, Have you tried to install it that way.

---

### Post by neu2buntu on 2011-05-20
your issue looks like you did not do the build inside the ~/lmms folder, you have just created build file in your home ( ~/ ) folder, so you should do ```
cd lmms
``` then the rest of the commands

---

### Post by Gabriel777 on 2011-06-02
Hey

I had the same problem starting out with Ubuntu today. I realised i didnt even have to use the terminal. I just went into the Ubuntu Softwarecenter in the Programs desktop tab, and found it in there. 

It runs out of the Terminal, which means i cant close the terminal. But it works.

---


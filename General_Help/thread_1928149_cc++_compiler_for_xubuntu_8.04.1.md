---
title: "c/c++ compiler for xubuntu 8.04.1"
date: 2012-02-19
forum: General Help
---

### Post by meridius10 on 2012-02-19
I am trying to install a C and C++ compiler for xubuntu 8.04.1 which I installed on an old laptop using the alternative install method.
 
If I try the instructions here:
 
[http://www.wikihow.com/Compile-a-C/C%2B%2B-Program-in-Ubuntu](http://www.wikihow.com/Compile-a-C/C%2B%2B-Program-in-Ubuntu)
 
I get:
 
```
E: Couldn't find package build-essential
```
 
If I try this:
 
[http://ubuntuforums.org/showthread.php?t=861215&page=5](http://ubuntuforums.org/showthread.php?t=861215&page=5)
 
and start by typing this:
 
```
sudo gedit /etc/apt/sources.list
```
 
I get the message:
 
```
sudo: gedit: command not found
```
 
I am trying to avoid putting this laptop on the internet.
 
Any ideas?

---

### Post by muteXe on 2012-02-19
Just to be clear: You're trying to run 
```

sudo apt-get install build-essential

```

whilst *not* connected to the internet?

---

### Post by forrestcupp on 2012-02-19
You can't download and install any programs from the repos without being connected to the internet.

I'm not sure whether Xubuntu comes with gedit preinstalled or not.

---

### Post by meridius10 on 2012-02-19
Can I download whatever is needed (whatever that is - a compiler?) from another computer and put it on a USB and install in xubuntu?

---

### Post by meridius10 on 2012-02-19
OK - just some additional information.
 
If I put ```
gcc-v
``` I get the version as ```
gcc version 4.2.3 (Ubuntu 4.2.3-2ubuntu7)
```
 
If I ```
cd
``` to the hello.c document and ```
gcc hello.c
``` or ```
gcc hello.c -o hello.exe
``` I get:
 
```
 
...stdio.h: No such file or directory
incompatible implicit declaration of built-in function 'printf'
no newline at end of file... 

```
 
so it must be picking something up.

---

### Post by forrestcupp on 2012-02-19
Your best bet to be able to install something offline is APTonCD. It's in the repos. With it, you can install whatever packages you want on a computer that *is* connected, then use APTonCD on that computer to create a repository of installed debs with their dependencies on CDs so that you can then install those packages on a computer that is offline.

You can download the deb file for [APTonCD right here](https://launchpad.net/ubuntu/oneiric/+package/aptoncd) to install on your offline computer. Hopefully it doesn't have any dependencies you don't already have. With this you should be able to install build-essential and everything it points to on your computer that is online, then install it to your offline laptop.

---

### Post by meridius10 on 2012-02-19
Not sure I get this - sounds a little complicated for a novice like me.
 
Is there a simpler way of resolving the problem? I can't understand why things aren't working with my current setup.
 
I found a link here and tried what they said but no luck:
 
[https://answers.launchpad.net/ubuntu/+question/17804](https://answers.launchpad.net/ubuntu/+question/17804)
 
That is a mirror image of my problem except with no success as when I try ```
sudo aptitude install build-essential 
```I get the msg:
 
*Couldn't find any package whose name or description matched "build-essential".*
 
Is the above sudo command dependent on an internet connection?
 
Worst case scenario - I know my mobile dongle works on the latest version of Ubuntu, so I am guessing that would also work on the latest version of Xubuntu as well?
 
I would then need to find a download of the latest version Xubuntu (alternate install as the laptop only has 160MB RAM and that is the maximum!!!) and try to get an internet connection, but only if this is the root cause of the problem.
 
My main computer is on Windows.

---

### Post by oldos2er on 2012-02-19
Support has ended for 8.04.1, its repositories have moved to old-releases.

[http://www.snowfrog.net/2009/05/02/apt-sourceslist-for-old-versions-of-ubuntu/](http://www.snowfrog.net/2009/05/02/apt-sourceslist-for-old-versions-of-ubuntu/)

---

### Post by jacob.david on 2012-02-19
> sudo gedit /etc/apt/sources.list

For this to work, gedit should have sudo access. Has this been granted?

---

### Post by forrestcupp on 2012-02-19
> **meridius10 said:**
> 
 
Is the above sudo command dependent on an internet connection?

Yes. Aptitude is dependent on an internet connection, too. You basically can't install anything without an internet connection unless you want to get real complicated. APTonCD is the least complicated way to do it, and it's not really easy.

One of the things about Ubuntu is that it's not a great experience without an internet connection, unless you only need what comes preinstalled. But if the latest Ubuntu works with your wireless dongle, Xubuntu probably will, too.

Your problem is that you have GCC installed, but you don't have a lot of other necessary things installed. You're best off to try to get some kind of internet connection on there, even if it's temporary. That's going to be the easiest way.

---

### Post by meridius10 on 2012-02-20
It looks like an internet connection may be necessary.
 
Is it possible to find something to download that will get me the same internet connection, but install it in 8.04 rather than doing a fresh install of the latest version of Xubuntu? My laptop only has 160MB max and I'm not sure it will survive the latest version of Xubuntu.

---

### Post by meridius10 on 2012-02-20
```
sudo gedit /etc/apt/sources.list
``` 
 
> **jacob.david said:**
> For this to work, gedit should have sudo access. Has this been granted?
 
If I put that in the terminal, I am asked for my sudo password. After I enter it I get the msg:
 
```
 
sudo: gedit: command not found

```

---

### Post by Vaphell on 2012-02-20
there is no gedit in xfce, use the name of the default xfce text editor instead (mousepad?)

---

### Post by meridius10 on 2012-02-20
If I put in:
 
```
sudo mousepad /etc/apt/sources.lst
```
 
I get a blank sources.lst mousepad file with a red warning sign saying:
 
'Warning, you are using the root account, you may harm your system.'
 
However, I can physically get into the file using a password.
 
Something is written about being able to install from the CD-ROM. Source code is not clicked. I am not sure what to do next.

---

### Post by meridius10 on 2012-02-23
OK - one step forward. I installed Xubuntu 11.10 (alternate install disk). The latest version does actually work on 160MB RAM!
 
I got an internet connection although I don't think this 
 
```
 sudo aptitude install build-essential 
```
 
picked up anything.
 
I managed to complile a C program. I tried to do a C++ one but got a msg saying:
 
"The program 'C++' can be found in the following packages:
* g++
* clang
* pentium builder
Try sudo apt-get install <select package>"
 
I tried this with each package but didn't manage to be able to compile C++. I am not sure if anything was downloaded or if these packages are already installed. I wonder if there is another way around this and if there is anything I can install from the Software Centre.
 
Also I don't understand how to 'cd' to the actual folder to compile. I can do this by right clicking on the folder and selecting "Open Terminal Here" which selects the location myusername@mynetworkname **~/Documents$. **However, I am wondering how I can get to **~/Documents$ **myself through the cd command.

---

### Post by oldos2er on 2012-02-23
```
cd Documents
``` will get you there if you're in your /home/user folder. If not, use ```
cd ~/Documents
``` The ~ is short for /home/user.

[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

---

### Post by meridius10 on 2012-02-23
Thanks - that worked.
 
Now I need to figure out the C++ compiler bit...

---

### Post by oldos2er on 2012-02-23
I'd install the g++ package, it's most likely the one you need.

---

### Post by meridius10 on 2012-02-23
What's the best way to do this as ```
sudo apt-get install g++
``` and ```
sudo aptitude install build-essential
``` didn't work?

---

### Post by oldos2er on 2012-02-23
Can you post the output from ```
sudo apt-get update && sudo apt-get install g++
``` ?

---

### Post by meridius10 on 2012-02-24
I managed to get the above commands updating with an internet connection so everything is OK now and I am able to compile in C and C++. :D

---


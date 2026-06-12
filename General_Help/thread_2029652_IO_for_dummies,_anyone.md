---
title: "I/O for dummies, anyone?"
date: 2012-07-20
forum: General Help
---

### Post by Amightyboar on 2012-07-20
Hi friends :)

I am new to Linux, and although you're all probably used to seeing new kids ask for help that they really should know, I have a kind of problem that can't be found with a simple Google search (at least with my attempts). After scouring this forum for a time, I discovered that most of the people here are so much more competent than pretty much everywhere else. But enough about that; my problem is this:

My first-year engineering professor designed an I/O board task for us (the students) to practice c++ code with. Basically you have to plug in your ousb board, enter a bunch of things in a terminal window and voila, you have a tiny lights show. He provided us with a Linux Mint live DVD to practice our code skillz with, but unfortunately my laptop pretty much instantly rejected it (I could not for the life of me get the wireless card to work). I have since then installed the very latest version of Kubuntu and it works perfectly except for one problem, the ousb application that my professor provided to use is giving me hell.

This is how the task is supposed to go:  1. plug in ousb board
2. download a file from my professors website: "http://pjradcliffe.wordpress.com/open-usb-io/resources/"
3. if you're on Windows, run the .exe and you're good to go, and if on Linux copy and paste the file into a specific place
4. Type the following in a terminal window:
ousb io portb <somenumber>
5. Enjoy the LED lights

I have tried this on Windows and Linux Mint and it works fine (all these on the same laptop), now I have installed Kubuntu but when I do all these steps I get this:

amightyboar@aToaster:~$ ousb io portb
bash: /usr/local/bin/ousb: No such file or directory

(Yes my computers name is aToaster :P)

I've followed the instructions at:
[http://pjradcliffe.files.wordpress.com/2009/04/open-usb-io_reference_1v083.pdf](http://pjradcliffe.files.wordpress.com/2009/04/open-usb-io_reference_1v083.pdf)

perfectly, but I always get this error. Why is it telling me there is no file called 'ousb' in the directory /usr/local/bin?
I am literally looking at the file in the correct directory right now, nothing is misspelt or incorrect case. I previously got the error 'Permission denied' when running the terminal command, but then I just opened Dolphin, navigated to the directory containing ousb, and changed up the permissions myself, now when I run the very same command I get a message saying No such file or directory? Why?:confused:

---

### Post by M!K3_$ on 2012-07-20
> **Amightyboar said:**
> 
amightyboar@aToaster:~$ ousb io portb
bash: /usr/local/bin/ousb: No such file or directory


Perhaps you should use the full file path of your ousb script. Or if you are in the same directory as the script you can use:
```
./ousb io portb
```

---

### Post by M!K3_$ on 2012-07-20
Even better....  this is copied out of the pdf:
> Calling issues: in the examples below the program ousb is assumed to run from the Linux path.
For Linux only, if the version of ousb to use must come from the current working directory then
use ./ousb rather than ousb which is used in the examples below.
For Windows use ousb which can be either in the current path or the active directory.
Under Linux the ousb program must have its permissions set to executable, there is no such
requirement under Windows.


---

### Post by Amightyboar on 2012-07-20
It works!!! I'm completely embarrassed, thank you sir!

May I ask, what is the function of ./? Is it a linux thang?

---

### Post by M!K3_$ on 2012-07-20
The period repressents the current working directory.

For example if you had your script in your home directory (and your current working directory was /home/amightboar) you could either use a full path, or a relative path (relative to your current working directory).
```
/home/amightyboar/ousb
```
```
./ousb
```


You can view your current working directory with the "print working directory" command ```
pwd
```

---

### Post by richpri on 2012-07-20
For a bit more info about relative path names see:

[http://linux.about.com/od/itl_guide/a/gdeitl29t01.htm](http://linux.about.com/od/itl_guide/a/gdeitl29t01.htm)

---


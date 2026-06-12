---
title: "Ubuntu Freezing"
date: 2009-11-09
forum: General Help
---

### Post by risnercharles on 2009-11-09
Hi all I recently made the switch from the dreadful windows to ubuntu and have to say i love the OS,that being said i am having an issue 
when starting to run some programs the system stops responding
the mouse does move but i cant click on anything and keyboard does not respond doesn't even light up for caps lock

it first happened when running firefox with google search bar so i done so searching and found a post saying there where some issues with the google bar so i removed firefox completely lol and still didnt fix it but it hasn't frozen while on the web at least not yet,but the last couple of times it has done this was while trying to load certain programs like a firewall or certain games i was wondering if maybe i had tried to run a program that was to much for my system but my system falls in at least with the min requirements.

I was just wondering if this was a bug or if someone else has been having the same issue thank you in advance.

---

### Post by bashphoenux on 2009-11-09
i dont face such problems mate !! did you do a fresh install ??

---

### Post by Johnsie on 2009-11-09
I've had this problem too and I know there is another thread relating to this. I'll just look it up.

---

### Post by risnercharles on 2009-11-09
yes i done a complete reformat downloaded from ubuntu and installed done the updates then it started to happen

sorry if there is another thread relating to this i tried to search but couldn't find anything

---

### Post by risnercharles on 2009-11-09
thank you guys for your responses.
after doing some searching, and reading a lot of the other threads i have came to the 
conclusion that this may have something to do with my hardware so i am going to try 
xubuntu and maybe mint to see if my hardware is causing this issue i will report if this 
fixes the problem.

---

### Post by bchurchill on 2009-11-09
There are all sorts of things that could be wrong - usually hardware/driver related.  Next time it freezes, reboot and run the following commands:

sudo cat /var/log/system.log | tail
sudo cat /var/log/dmesg.log | tail
sudo cat /var/log/messages.log | tail

Post the output here so we can try and figure out what's wrong.

---

### Post by bchurchill on 2009-11-09
> **risnercharles said:**
> thank you guys for your responses.
after doing some searching, and reading a lot of the other threads i have came to the 
conclusion that this may have something to do with my hardware so i am going to try 
xubuntu and maybe mint to see if my hardware is causing this issue i will report if this 
fixes the problem.

xubuntu almost definitely won't solve the problem - everything is the same under the hood, it's just a different desktop interface.  mint has a slightly better chance, but you're probably going to deal with similar issues.  I suggest you try and troubleshoot it on Ubuntu, but it's up to you.

---

### Post by risnercharles on 2009-11-09
well i would like to use keep using ubuntu so i guess i will just do a trial and error with my programs and, thank you for the log commands and i will post the log files if it fails again 
should i post it in this thread or is there a forum dedicated to log errors?

---

### Post by bchurchill on 2009-11-09
> **risnercharles said:**
> well i would like to use keep using ubuntu so i guess i will just do a trial and error with my programs and, thank you for the log commands and i will post the log files if it fails again 
should i post it in this thread or is there a forum dedicated to log errors?

This thread will work fine.  Nobody really understands everything in them, but there's usually enough information that someone (possibly yourself) can find the faulty component.  Usually it'll come down to searching for a new driver for something or another...  I've had this exact same issue with both a faulty video card driver and a faulty wireless card driver.  Another thing that might help is the output of

lspci

---

### Post by risnercharles on 2009-11-09
i remember looking at the system log viewer after the first time it crashed it had an error called /var/log/btmp this file is not a regular file or text file 

i done a search and it led me to this site and thats when i got side tracked lol and just remembered it 

also about the driver's is there anyway to view the installed drivers and update them like you can in windows or is there a certain program i can download to allow me to do this?

---

### Post by bchurchill on 2009-11-09
> **risnercharles said:**
> i remember looking at the system log viewer after the first time it crashed it had an error called /var/log/btmp this file is not a regular file or text file 

i done a search and it led me to this site and thats when i got side tracked lol and just remembered it 

also about the driver's is there anyway to view the installed drivers and update them like you can in windows or is there a certain program i can download to allow me to do this?

Normally drivers are included in the linux kernel - this is what makes most of your hardware work, and kernel drivers usually are quite good.  The issue is that sometimes drivers aren't included in the kernel because they're very new or because they're proprietary and can't be included with the kernel due to licensing issues (nVidia video, for example).  Unfortunately there's no centralized way to deal with drivers that are outdated in the kernel, at least not that I know of.  

If you can't reproduce the error soon, I would recommend googling your wireless card and/or your video card to see what the latest drivers are, and if crashes are known for your current hardware/driver situation.

---

### Post by risnercharles on 2009-11-12
thank you everyone for your help 
yesterday after sometime of searching i figured i would try to do another clean install but with the same issues then i came across  a thread that was of some help [http://swiss.ubuntuforums.org/showthread.php?p=8293656](http://swiss.ubuntuforums.org/showthread.php?p=8293656)  i installed the kernels and that fixed the problem  but now i dont have any sound.. im clueless as to what i need to do any help would be appreciated.

---


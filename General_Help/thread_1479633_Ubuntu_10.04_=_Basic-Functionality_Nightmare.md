---
title: "Ubuntu 10.04 = Basic-Functionality Nightmare"
date: 2010-05-10
forum: General Help
---

### Post by flowingfire on 2010-05-10
I regret installing Ubuntu 10.04.  Ubuntu 9 worked perfectly. I will outline why, for me, this new version has been a basic-functionality nightmare. 

[U][B]
Problem 1: Installation[/B][/U]
First, I couldn't load the live CD whatsoever.  Black screen, non-responsive.  It would show a brief purple screen, then go dark every time.

I spent four hours trying to figure out how to get it working on the forums and on chat.  Finally, I found directions to fix this problem.  (And no, it was not a problem with the media.)

Step 1: Wait until the purple screen flashes when the live cd is in the drive.  Then, quickly press the spacebar to bring up the menu.  

Step 2: Do not access anything on the menu, because it will black-screen.  Instead press F6, and choose "nomodeset."  Then, go into the installation.  

Step 3: Once installed, press "e" in the grub menu and type "nomodeset" after "quiet splash."  This allows you to boot at all.  

Step 4:  Once inside Ubuntu, open the terminal and type "gksudo gedit /etc/default/grub"  

Step 5: In the grub file, replace GRUB_CMDLINE_LINUX_DEFAULT="quiet spalsh" with "GRUB_CMDLINE_LINUX_DEFAULT="nomodeset"


**_Problem 2: Display _**
The display isn't correct, off-center, and distorted in parts.  So, I attempt to solve this by doing the following:

Step 1: I go to the "Ubuntu Software Center."
Step 2: I select to download and install the newest NVIDIA proprietary driver.  
Step 3: It instructs me to type some gobble-de-gook into the terminal, which I do.  Now the NVIDIA driver is installed.

Unfortunately, the proprietary driver (notably the same one that worked perfectly with Ubuntu 8 and 9) crashes on boot-up all the time.  It works whenever it feels like it, sometimes presenting me with an error dialogue on startup and sometimes loading fine.

So, I just know now that whenever I boot, Ubuntu will choose to play nicely with my NVIDIA graphics card or not.


**_Problem 3: Internet / Network_**
The Internet does not work.  Actually it only works when it feels like it, which makes the problem even more frustrating.  

Notably, the Internet connection is fine according to Ubuntu.  Pings work through the terminal.  The wireless manager in the upper-right corner of Ubuntu says I'm connected to my network with excellent signal strength.

Unfortunately, software updates aren't working.  Firefox times out and says it's unable to connect to any webpage.  No web application works.

And yet, I might get a 30-second window once-in a while when I can pull up a webpage and surf... Until it stops working again. 

My connection is fine.  The router is fine.  The same Internet connection works perfectly on the same computer, on WINDOWS.  What?  I still haven't figured this one out.


I have spent nearly 10 hours just trying to get basic functionality out of Ubuntu 10... No wonder it's called Ubuntu 10.... I may have used Ubuntu for many years, but I still can't figure this crap out!


Come on!  After having the previous version of Ubuntu work perfectly, this operating system wouldn't install without immense research, wouldn't display properly, crashes now that I got it to display properly, won't connect to the Internet, and continuously gives me all sorts of other strangeness.

Two.  Thumbs.  Down.

---

### Post by flowingfire on 2010-05-16
Update: I still haven't figured out how to get the proprietary Nvidia driver to stick and function.  It will work, and then on random statups, crash the x-server, and not boot without resetting xorg.conf... 

This, of course, means I have to start all over again.

In Kubuntu, when I installed it, the proprietary nvidia driver doesn't work at all.

Even after using Ubuntu for years and being a moderately informed user-- though not proficient with command line-- I cannot get this working.

I've done complicated stuff on here like wrapping drivers and compiling them, but I can't get my internet and display to work.  great.

---

### Post by kevinatkins on 2010-05-16
This sounds like a nightmare.

I'm tired and about to head for bed, but I'd suggest you get some hardware specs posted. I've had less trouble with 10.04 than with some of the earlier releases, on numerous machines, so I'm puzzled..

---

### Post by JigglyWiggly_ on 2010-05-16
Go back to 9.10 please, I am getting a headache reading that, I imagine your frustration.
10.4 is the buggiest release of Ubuntu I have noticed:
Disaligned a RAID 5 array, disk utility disaligns RAID on setup.
Couldn't get multiple displays working.
Buttons on the wrong side of the window. (Not a bug)
Internet works intermmitenly on a x48 chipset

Yeah... 9.10 worked nicely.
It's funny that 10.4 is a LTS. I would much rather stick with 8.04 LTS or Debian 5.

---

### Post by Yappy on 2010-09-20
Yes 9.10 works fine... but not 10.04

---

### Post by KajuNM on 2010-09-20
That's what I did today, I went back to 9.10. I hope 10.10 will be better than 10.04. But I'll wait until 9.10 isn't supported anymore. Then I'll probably switch to another version......

---

### Post by hawthornso23 on 2010-09-20
10.04 works fine for lots of people. I'm having no trouble with it.

---

### Post by Elfy on 2010-09-20
No need to bump this - it's not a support request.

Closed

---


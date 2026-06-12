---
title: "ATI Radeon HD 5xxx w/ Blank screen on Lucid install/upgrade (Workaround/SOLVED)"
date: 2010-09-29
forum: General Help
---

### Post by jason.m on 2010-09-29
After scouring the internet for a solution, I finally came up with this on my own. I figured I would post it for all. Also, and perhaps this only happens on the MacPro, other solutions present out there; adjusting kernel options: radeon.modeset=0, nomodeset=0, install 9.10 and then upgrade to 10.04 (but only after telling 9.10 NEVER to update the X server libraries (strangely that worked until a 10.04 kernel update)) and the like, did not help me. So for my very first post to this forum... here we go:

**Symptoms:**

Installation of Ubuntu 10.04 starts correctly then kills the display immediately after starting the graphical installer (goes to sleep/blank screen)
Installation of the Ubuntu 10.04 alternate installer (text based) installs fine, but once complete boots to a blank screen

Installation of Ubuntu 9.10 works correctly.


**Systems Effected:**
MacPro late 2009 
MacPro early 2010
Dell Precision 490 (year 2006/2007)
Dell Precision T7500 (year 2010)
Any PC using the ATI Radeon HD 5xxx (The four PCs I tested anyway)

As you can see, a very wide range on computers indeed. Thus, this points at the video card exclusively (or actually Lucid, since Karmic works just fine)

I could be completely wrong about this next point (Flame/Commit all you want):
Going through the Xorg logs, I found that the display is properly detected (DELL 30 inch, model number, serial number and all), but was giving the physical resolution of 627x422 (which can not be displayed on LCDs)
This makes me believe that an older CRT monitor may actually work! (if you have one, please try it and report)


**Tools needed:**

A separate working Linux computer with X windows installed
An active Internet connection
Network Switch w/cables (to connect both Linux machines to the Internet and each other)


**Steps:**

0. (connect all PCs to network switch and verify a working Internet connection with the working Linux machine)... dah

1. Install Ubuntu 10.04 using the alternate disc (text based). You can get the alternate disc here:[INDENT][http://ubuntu.cs.utah.edu/releases/lucid/](http://ubuntu.cs.utah.edu/releases/lucid/)
[/INDENT]2. Complete the installation with the exception of:[INDENT]     a. Manually entering the network IP address (do not configure for DHCP. Or do configure for DHCP if you want, but there will be more steps)
[/INDENT]3. Reboot as requested to finish the installation and allow the machine to completely boot (to a blank screen... DOH!)

4. Although the machine appears non-functional (blank screen) perform the following very carefully:[INDENT]     a. Drop to a full TTY terminal (ctrl-alt-F1)
[/INDENT][INDENT]     b. enter your user id then strike enter
[/INDENT][INDENT]     c. enter your password then strike enter
[/INDENT][INDENT]     d. enter *apt-update* and strike enter (then wait a good few minutes depending on your Internet connection to complete)
[/INDENT][INDENT]     e. enter *apt-get install openssh-server* (then wait a good few seconds depending on your Internet connection to complete)
[/INDENT][INDENT]     f. enter 'y' and strike enter to accept the installation of the openssh-server (then wait a good few minutes depending on your Internet connection to complete)
[/INDENT]Yeah... ugly. Its completely 'I think its done or ready...', but we MUST get openssh installed. I tried to force the alternate install disc to allow the installation of additional software, but I couldn't find it. <edit please if someone knows>

If you must use DHCP (like I do in our work environment) if not skip to step 4:[INDENT]     g. at this point, try to SSH from the blank screen machine to your working machine...: *ssh someuserid@workinglinux's_ip-address*
[/INDENT][INDENT]     h. from the working Linux machine, drop to a terminal prompt and enter: who   This will show you currently logged in folks. Were looking for the IP address of the blank screen Linux PC.
[/INDENT]Yes, I know there are many cooler ways of tracking down that rouge IP; tcpdump, logging into your network switch, running a dhcp server from the good Linux box and checking the leases... Basically just do what EVER you can to determine the blank screen Linux's IP address and go to the next step.

4. Using the other working Linux computer:[INDENT]     a. Drop to a full TTY terminal (ctrl-alt-F1)
[/INDENT][INDENT]     b. enter the command: *xinit -- :1*
[/INDENT][INDENT]     c. In this mode, you will have to have your mouse actually hovering over the terminal window, in order to type in it :)
[/INDENT][INDENT]     d. enter *ssh -X userid_of_blank_screen_linux@IP_address_of_blank_screen_linux* (and log in as normal)
[/INDENT][INDENT]     e. once logged in remotely, enter: *gnome-session* and strike enter
[/INDENT]This will start X and grant you a remote control of blank screen. From here, very easily, click on System, Hardware drivers, and select the ATI video card, and choose to activate driver. Reboot and enjoy.:guitar:

Ahem... sometimes (once) I had to perform in addition, after the reboot:[INDENT]*aticonfig --initial*
*aticonfig --resolution 0,2560x1600*   (obviously put what you need there)
*reboot*
[/INDENT][B]
Thoughts:
[/B]
Better ways to install openSSH?
Better ways to activate the ATI hardware remotely from terminal, and not having to remote start a graphical X through port forwarding (even though its cool, and for some of you, you might be thinking "I can do that?!?! SWEET! Thanks!)?

This has been fully testing on all four of those previously listed machines, with kernel updates and the like afterwards with no issues.

---

### Post by sendblink23 on 2010-10-02
I think its more basic to simply install 9.10, then afterwards install the FGLRX driver... then do the upgrade to 10.04 LTS... and the display will work perfectly fine after upgrading :P

---

### Post by jason.m on 2010-11-01
I do remember an older post suggesting to:
 
install 9.10, open synaptic package manager, selecting all x11 packages, and choosing to "taboo" the packages (basically telling the system to never update x11).
 
Then, upgrade to 10.04 normally. The update will not touch the x11 sub-system.
 
That trick DID worked for me (and I wish I could remember the forum). However, and silly me :), once 10.04 was installed, what do we all do? Perform an update! LOL
 
I completely forgot to go and re-taboo the x11 sub-system. But reading over my notes, I realized that if I would have installed the fglrx driver 'before' performing the 10.04 update, I would of been fine.
 
Upgrading from 9.10 would work as you suggested, but for some reason, I had to perform the extra step of leaving the x11 sub system un-changed.
 
-stupid computers.
 
I know there are many posts out there that are solving this issue in other very simple ways. I only posted my solution to try and help possibly another tech whom was having the same issues as me...

---


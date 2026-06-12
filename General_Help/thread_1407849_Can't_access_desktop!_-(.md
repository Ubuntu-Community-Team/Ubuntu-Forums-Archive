---
title: "Can't access desktop! :-("
date: 2010-02-15
forum: General Help
---

### Post by fleppmar on 2010-02-15
Hi!

Today i purged and renistalled nautilus because I wanted to see if I could get my desktp icons back. 
After the reboot, I continue to login, and after i login ubuntu 9.10 goes into terminal and nothing else. 

What commands do I need to fix this?
Im online on my phone now. Haha! ;-)

thanks! 
Regards
fleppmar

---

### Post by bwhite82 on 2010-02-15
From the command line, I would give this a try:

> sudo dpkg-reconfigure nautilus

Then:

> startx

---

### Post by fleppmar on 2010-02-15
Hi. 

Tried it and got this message:
X: user not autorized to run the X server, aborting.

---

### Post by bwhite82 on 2010-02-15
Then reconfigure that package too!

> sudo dpkg-reconfigure xserver-xorg

---

### Post by fleppmar on 2010-02-15
Nothing happens when I try that.

Tried to reinstall with sudo apt-get install xserver-xorg
It says that it is installed.

But get this error:
Fatal Server error
Server is already active for display 0.
It this server is no longer running, remove /tmp/.X0-lock
 tried many different combos to remove it. Nothing works. :-/

I remove, reinstalled, and tried to reconfigure. Nothing works. :(

---

### Post by Neroli on 2010-03-07
Did you ever get around to fixing this? The thread name is tagged [SOLVED] but you haven't listed any solution that worked for you.

I'm interested to see if you did wind up solving it on your own in the end, and how. I'm having a similar issue since I tried to upgrade to the alpha release of Lucid Lynx - when the computer boots up, I only get a command line interface. I tried the options listed in this thread but while they have allowed me to load my desktop (with my background, saved items etc) I can't actually *do* anything. I try moving the trackpad of my laptop and the pointer stays firmly in the centre of the screen. I try typing and nothing happens.

I would probably create a new thread for my own issue as I can't seem to find anyone else with uniquely similar problems; I thought I would at least try asking you if you did sort the issue out after all, however, as it would save a lot of hassle.

---

### Post by fleppmar on 2010-03-07
Hey, man!

Sorry, I dont have a solution for you. My entire system just got more and more mental, so I had to reinstall everything.

---

### Post by Neroli on 2010-03-09
Eh, not to worry - mine too. I've decided to run with a dual boot of Windows 7 and Lucid so I guess in the end it gave me the opportunity to start over, at the very least. Oh well.

---


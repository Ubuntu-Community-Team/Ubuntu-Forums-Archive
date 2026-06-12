---
title: "What happened to my original setup?"
date: 2012-01-18
forum: General Help
---

### Post by iamsamami on 2012-01-18
Greetings,
I am relatively new to Linux, about a year getting kinda familiar with it, how to get around in it, yet still a little scared to play with command line operations. I've been able to get online at the library, synaptic really helps me to download pretty well, and usally find a way to figure out why something doesn't seem right - usually cause I'm still famliar to windows.
 
O.K., but now something has happened that's totally tripping me out. My normal startup and login is still the same, so it was a while later before I noticed a WHOLE LOT had changed. 
My top line panel is different, choices and preferences are totally different.
I can not shutdown normally. As I attempt to - it retarts and I am forced to login in with password to continue - else use power switch to turn off.
Everything seems to run slower, or response is slower.
I cannot open many applications; Synaptic, Backup Restore, Backup Configure, ...
I cannot find a way (yet) to open the network to get online with my Linux Netbook; I have to use their computers to make this post and I only got 10 minutes left.
It's like my computer somehow opened a whole different version even after turning on and off a couple times since last visit online; though I did use Synaptic then to install "Stellarium." Only opened it once but not yet since and don't really thinks that's the source of problem.
4 mins. left, goto go for now.
I will get back to here when I can, but it is often sporatic when I get into town long enough to come to the library. 
Please help me figure this out. Send me links to info, troublshooting etc.
 
thanks much,
IamSamamI

---

### Post by cariboo on 2012-01-18
What version are you using? Can you log into a different desktop environment from the login screen?

---

### Post by adrien214 on 2012-01-18
Did you enable auto-login by any chance? If yes, start a terminal and type in 

```
gksudo gnome-control-center
```

click on User Accounts and select your normal user then disable auto login. If you cannot do this from your current session, do the same from the guest session.


If the above does not work, try

```
sudo dpkg-reconfigure lightdm
```

and set it up to use gdm.

hope this helps.

---

### Post by iamsamami on 2012-01-26
> **cariboo907 said:**
> What version are you using? Can you log into a different desktop environment from the login screen?
 
[COLOR=black][FONT=Verdana]I finally got back into town to answer replies.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]When I login, initially my UBUNTU 2.6… starts up – then I begin to notice many differences, whether I start up with Ubuntu regular edition or Ubuntu second edition; but that applies to the GUI.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]I’m not that much CLI inclined. Only enough to have an idea of it.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]I cannot login as root, I never got that password, or su, I can’t remember that password and can’t remember how to reset it or get around it that way.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Out of the messages in the log file I see a lot of reference to ”Failed to load “module-console-kit.c””[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]I cannot open several applications somehow tied in with needing root or su privileges; also cannot open a usb flash drive, nor a usb HD reader, and I have no cd player attached. Top it off, I can’t find the app or widget to open a wifi line to get online. I have to use this town’s library computer and time is limited.[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]I’m thinking I need to at least get su to let me make any changes. If I can get usb to read a flash drive I could at least save a lot of files before I nuke this one out and get it all set up right.[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]BUT, I can read a flash drive in the boot options. I've got a copy on one but I didn't make it bootable. That's something I'm working at next. But if I do that, will I be able to re-install on top of existing; or will it create a whole clean install and everything is gone.[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]One other thing. I'm thinking that my netbook's sound card maybe burned out. I noticed a different sound driver got selected and then start noticing that after a few hours of playing – it starts making weird interruptions and then Rythmbox stops responding. If I kill R-box and restart it, it works again.[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]I don’t know. This is all too much for me. But I have to get this netbook to work again. It is my connection to my world away from the ranch.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Time is up for now. Will try to get back online sooner with any additional info I can gather.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Thanks,[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]IamSamAmI[/FONT][/COLOR]

---

### Post by iamsamami on 2012-01-26
I tried both, niether worked. I need to get get su somehow
!????!

---

### Post by dcstar on 2012-01-27
> **iamsamami said:**
> 
...........
O.K., but now something has happened that's totally tripping me out. My normal startup and login is still the same, so it was a while later before I noticed a WHOLE LOT had changed. 
My top line panel is different, choices and preferences are totally different.
I can not shutdown normally. As I attempt to - it retarts and I am forced to login in with password to continue - **else use power switch to turn off**.
..........

Doing that is just about 100% guaranteed to break your system and cause the issues you are describing.

Boot off a Live CD/USB and do a fsck/Disk Check on the Ubuntu partitions. Then search out instructions for backing up your /home data to be used after reinstalling Ubuntu.

---


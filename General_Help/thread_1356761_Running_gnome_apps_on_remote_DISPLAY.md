---
title: "Running gnome apps on remote DISPLAY"
date: 2009-12-16
forum: General Help
---

### Post by benkid77 on 2009-12-16
Hi all,
 
I have Ubuntu karmic installed on a home computer which is switched on all the time and its primary purpose is acting as a low-traffic webserver and mailserver on an ADSL link (just for some non-critical hobbyist stuff). However, I also like to remotely run some gnome apps on it from my workplace. A good example is gnome-sudoku.
 
In my workplace, Windows is used on our desktop PCs and so I have set up two methods of connecting to my home Ubunutu PC so I can run my Linux apps remotely whilst at work.
 
Method 1: I connect to home PC via SSH using PuTTY and I also have the free "Mocha X server" installed on my work PC which allows me to run individual X applications, such that they appear integrated into the Windows session.
 
Method 2: I also use nomachine NX client to connect to FreeNX server running on my home PC, allowing me to get an entire Gnome session within a single Windows window.
 
Both of the above methods work absolutely fine for all non-gnome X-windows apps (e.g. xeyes, xcalc etc..) , however only method 2 works for gnome-sudoku (and a few other gnome apps).
 
I would much rather run some gnome apps using method 1, which integrates the apps better into my Windows environment via the Mocha X server, than having to start up an entire Gnome session via NXClient.
 
However, I get this type of error "Gconf error: .....**Failed to connect** to socket /tmp/dbus-G3priI9DCT " in the PuTTY terminal when trying to start up some gnome apps that way.
 
I have DISPLAY set up correctly, and I also tried setting up some othe variables like ORBIT_SOCKETDIR.
 
Is there anything else I can do to run these gnome apps via the PuTTY terminal and the X-server without having to start an NX session? 
 
The funny thing is if I start an NX session and then within it I change DISPLAY to point to my work PC I can launch gnome-sudoku from it so that it appears on the X server on the work PC and that works fine (which is how I want it). However, if I do exactly the same thing from PuTTY even with DISPLAY setup the same then it fails with the above error - meaning I have to start a full NX session just to launch gnome apps, which I'd rather avoid. 
 
Apologies if this description got overcomplicated.
 
Thanks very much for any possible help or thoughts on this,
 
benkid77

---

### Post by NT4usB on 2009-12-16
I use: ```
$ ssh -X (IP of remote PC)
``` when I want to run graphical apps from my remote box on my local machine.

---

### Post by benkid77 on 2009-12-16
> **NT4usB said:**
> I use: ```
$ ssh -X (IP of remote PC)
``` when I want to run graphical apps from my remote box on my local machine.
 
Thank you very much. That has completely solved my problem! (Well I did the equivalent which was to check the box "enable X11 forwarding" in my Windows PuTTY client).
 
I guess I carried over too many bad habits from my TELNET days, trying to run X apps over an unencrypted connection to an X-server tut tut - no wonder the gnome app didn't like it.
 
Much better to run through the SSH connection as you suggest and no manual setting of DISPLAY for me. I'm just a dinasour!
 
Thanks again. :)

---

### Post by NT4usB on 2009-12-16
Glad it worked for you.
I read your post a couple times, figured you knew what you were doing. 
So I wasn't sure you hadn't already tried x forwarding and I just missed it in the post...
Be sure to mark the post 'Solved' using the thread tools above.

---

### Post by benkid77 on 2009-12-16
Thread now marked as solved. Best regards, benkid77

---


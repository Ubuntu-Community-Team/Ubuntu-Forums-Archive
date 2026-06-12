---
title: "create vnc session from remote and come back from other machine"
date: 2011-06-12
forum: General Help
---

### Post by dieter-erich on 2011-06-12
Hi,
   I connect to my PC from remote via ssh and run a program that opens a number of windows. If the connection is interrupted and I reconnect there is no way of getting back to see the windows created before. 

How can I come back to my previous screen? I was thinking about vnc but do not really know how to do. Can I somehow start a VNC session, start the program, close the connection and come back later to see the results? Is all that possible from remote?

What I have tried so far:
start gnome session from local PC on the remote PC with gnome-panel
start a vnc session from within with (real)vnc 127.0.0.1
try to connect to the vnc session from remote with (real)vnc xxx.xxx.xxx.xxx
> this failed. I do not get the connection!

I suppose that 1) all the graphics for gnome is done on my local PC and 2) that there must be problem with the screen number 

Thanks for help, D-E

---

### Post by linuxinstalledfromhdd on 2011-06-12
> **dieter-erich said:**
> Hi,
   I connect to my PC from remote via ssh and run a program that opens a number of windows. If the connection is interrupted and I reconnect there is no way of getting back to see the windows created before. 

How can I come back to my previous screen? I was thinking about vnc but do not really know how to do. Can I somehow start a VNC session, start the program, close the connection and come back later to see the results? Is all that possible from remote?

What I have tried so far:
start gnome session from local PC on the remote PC with gnome-panel
start a vnc session from within with (real)vnc 127.0.0.1
try to connect to the vnc session from remote with (real)vnc xxx.xxx.xxx.xxx
> this failed. I do not get the connection!

I suppose that 1) all the graphics for gnome is done on my local PC and 2) that there must be problem with the screen number 

Thanks for help, D-E

This works great:

[http://cinderbox.net/2011/05/23/how-to-teamviewer-6-for-ubuntu-natty-and-maverick/](http://cinderbox.net/2011/05/23/how-to-teamviewer-6-for-ubuntu-natty-and-maverick/)

---

### Post by HermanAB on 2011-06-12
Use a program called 'screen'.

---

### Post by dieter-erich on 2011-06-12
Thanks a lot for your hints! The point is that I do not very well understand "screen" and it is no quite clear to me whether I shall see all the windows created by the program when resuming screen. So far I did not succeed. 

 Teamviewer is fine but I believe that someone has to grant access and this person has to be in front of the remote PC I want to connect to.....

So far I found that using 'remote desktop' and the realvnc client is doing most of what I need but I have to first login locally to the PC I want to connect to later and then just put the screen saver on or change to another user to leave my session open. Only then I can resume this session from remote via vnc. My questions thus brake down to the following:

Is it possible to do all the above from remote as as well? Is there a way of leaving a session open that I started entirely from remote, even when interrupting the connection? Would that be possible with 'screen'?

Thanks, D-E

---


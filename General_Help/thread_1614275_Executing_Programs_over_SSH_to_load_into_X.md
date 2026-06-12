---
title: "Executing Programs over SSH to load into X"
date: 2010-11-05
forum: General Help
---

### Post by technick on 2010-11-05
Hey guys / gals.. I have an interesting problem =)

I need to execute programs to load from a remote ssh session and have them load into the current X11 session. I won't need to interact with the process and will be executing everything from the same user account that is currently logged into Gnome.

For background purposes, this is what I need to accomplish. There is a monitoring machine that displays current information for phone queues, open tickets and important messages across a huge projector. Sometimes the programs freeze or crash and require someones to go plug in a keyboard / mouse and load the apps again. I would like to be able to sign into the machine remotely over ssh and just kill the processes and relaunch them back into the same X11 session without a gui (So I can do it from my phone). 

How can I do this?

Thanks in advance!

:)


UPDATE!!!!!

I have figured out how to make this work by using this thread here. 

[http://ubuntuforums.org/showthread.php?t=514054](http://ubuntuforums.org/showthread.php?t=514054)

Thanks!!

---

### Post by HermanAB on 2010-11-05
$ ssh -X -C -c blowfish user@server "gedit /etc/fstab"

$ ssh -X -C -c blowfish user@server gnome-panel

Assuming of course that the remote machine actually has Gnome and gedit installed.

---

### Post by grepcat on 2010-11-05
[http://www.vanemery.com/Linux/XoverSSH/X-over-SSH2.html](http://www.vanemery.com/Linux/XoverSSH/X-over-SSH2.html)

---

### Post by technick on 2010-11-05
My ssh client doesn't support X11 forwarding. Its SSH over an android phone.

The info provided above is if I was doing X11 forwarding. 

The goal is not to bring the application to my remote connection but to load it on the current X11 session that is open on tty7.

---

### Post by efflandt on 2010-11-05
You likely need to be logged in as the user who owns the display and **export DISPLAY=:0.0** before you execute whatever you want to run into the background.  Not sure if you need to use **nohup**.

Try that out on an ssh session to a local computer, so you can test and see the results.

---


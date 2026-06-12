---
title: "VNC and starting problems"
date: 2012-02-08
forum: General Help
---

### Post by Dschingis on 2012-02-08
Hello everyone,

Yesterday I set up a server, added vsftpd, ssh, httpd and everything works fine. The server should also connected to the network without a screen (which it currently does).

The problem is, I am still not that familiar to completly work on command line, so i wanted to add a VNC solution. Now I tried some possible solutions and everytime I ran into some problems:

#Solution 1: start a vncserver :1 in ssh and connect with vncviewer.
Problem: I can only see the desktop, no taskbar and can't do anything. Some ppl said this is a current problem with tightvnc so :/

#Solution 2: use vino and connect to :0
Problem: this works! but the user has to login which is a problem without screen :> (and vino won't start before a login) I also tried to create a vncserver :0 before login, but this screen is locked.

#Solution 2.1 boot into single user mode
don't like this solution and it doesn't seem to be that simple anyway so i discarded this.

So any ideas how to fix this? :)

Thanks

edit:
I forgot, I also tried some stuff with x11vnc (to start it in the ssh - which works with -noshm) also the tightvnc connection works - but then nothing happens in the viewer

---


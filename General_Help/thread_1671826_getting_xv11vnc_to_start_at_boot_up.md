---
title: "getting xv11vnc to start at boot up"
date: 2011-01-20
forum: General Help
---

### Post by jboris on 2011-01-20
I am posting this because I could not find any help on the forum. I did find a lot of threads about installing Tightvnc and a a lot of hacking needed but they were of no help. I did this very easily in Fedora but haven't been able to do this in Ubuntu. I am running Ubunto Server 64 Bit 10.04 LTS on an HP DL180 G5. I need to adminsiter this unit remotely and I would like to use the vnc server that came with it. Currently I have to login to the unit via ssh and do the following:
 
sudo x11vnc -display :0
 
Then I start my vnc viewer (RealVNC) and connect. At that point I get a password prompt and type in the password I set in the desktop preferences. After that the password dialog disappears and I have to walk down the hallway to the Network room and from the console enter a password. Once I do that and get back to my desk I have the VNC screen up with my desktop.
 
I want to be able to connect to the VNC session without all of those steps. Is there a good how-to for this somewhere? All pointers to such a document would be greatly appreciated.

---


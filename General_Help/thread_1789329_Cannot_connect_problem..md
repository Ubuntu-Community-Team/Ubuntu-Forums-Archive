---
title: "Cannot connect problem."
date: 2011-06-23
forum: General Help
---

### Post by Gahhruuba on 2011-06-23
New User to Ubuntu by the way, sorry you'll probably see me here quite a bit :popcorn:
I have two computers, both running Ubuntu 10.4 fully updated and I am trying to bring files from one computer to the other with Firezilla ftp client.
I was able to do this before, but I ended up having to reformat because  of a driver screwup that i couldnt figure out how to fix. Now I am at a loss on how I managed to allow the computer with the files to connect to the one receiving the files.
Computer A is the one that has the files that I am trying to send to computer B. Every time I try to send them over I get a "connection was refused" error. Typed in the right IP, username, password, and port but still wont connect.
Are there any things I have to do in terminal to allow access? I installed firestarter and just disabled it so ports should be open
By the way, I am using FTP because it was much simpler then trying to dink around with Samba  and this is a pretty safe network.

[Edit]
Enabled firewall, forwarded the ports in the events list then we get "request timed out"
[EDIT]
Reformated> Fresh install >Updated

---

### Post by Gahhruuba on 2011-06-23
[Bump]
So pretty much what i am trying to figure out here.. Is what steps do I have to do to allow an Ubuntu computer (latest versions) connect to my computer via FTP so we can drag and drop files from one computer to the other.
From a fresh install, just updated the system with Update Manager.
Please help me :/

---

### Post by Iowan on 2011-06-23
The FTP client comes with Ubuntu, but the server will need to be installed. There are a couple of versions available - or you can configure SSH, then use **sftp**.
[https://help.ubuntu.com/11.04/serverguide/C/ftp-server.html]("https://help.ubuntu.com/11.04/serverguide/C/ftp-server.html")
[https://help.ubuntu.com/11.04/serverguide/C/openssh-server.html]("https://help.ubuntu.com/11.04/serverguide/C/openssh-server.html")

Whilst looking through the server guide, I noticed NFS as another option.

---


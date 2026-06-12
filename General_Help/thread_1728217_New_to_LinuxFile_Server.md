---
title: "New to Linux/File Server"
date: 2011-04-13
forum: General Help
---

### Post by ter_smurf on 2011-04-13
Hi, I an new to Linux and Ubuntu. I do IT work for the schools so I'm pretty much in a Windows environment. This is totally new to me. Hard finding what I need to do in Ubuntu. I have version 10.10 Maverick. I just got a server that was donated to our dept. We want to use it for a file server so we can share files. What is the easiest way to do it with my Ubuntu? I am also using the desktop version. Will that be fine or do I have to use the server version? I installed the server version and after the install, all I got was a command promt. Couldn't do anything. I wanted the gui but everythign I tryed that people said, didn't work.

---

### Post by blueridgedog on 2011-04-13
Desktop will work, you may need to install a few server tools though.  Alternatively you can install server, then install the desktop environment. 

You can do that with:

```
sudo apt-get install ubuntu-desktop
```

To setup a file server, I suggest you start researching Samba.

This post shows how to set it up in a peer to peer environment:

[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

This is the actual site documentation as well:

[http://www.samba.org/samba/docs/](http://www.samba.org/samba/docs/)


You may have an authentication system that you can use in your existing network and will want to research that.  Once you thing you have your arms around the concept, you can start the install and configuration then post back individual problems or issues you encounter in the process.

---


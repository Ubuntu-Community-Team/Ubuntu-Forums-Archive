---
title: "Problem with FreeNX"
date: 2010-08-26
forum: General Help
---

### Post by loy66 on 2010-08-26
I have Ubuntu 10.04 (Lucid Lynx) computer with FreeNX server on it.  I am trying to access it from a Windows XP computer using NXcleint.  I get the WXP to connect with the Linux computer and I get the desktop screen. I have the two computers side by side for viewing my setup. On the Wxp I don't get the same screen that is showing on the Linux computer (Cannot see windows open etc.)  It is like I have a total independent system. I want to view the same display on both computers like in VNC which I am also trying.  It is my understanding that remote access using FreeNX would be faster and more secure than VNC over the internet.  Any suggestions on my problem?:(

---

### Post by som.mukherjee on 2010-09-01
i'm not an expert but i think when you connect via FreeNX, it actually opens a new session. Not exactly same as VNC. This is like same as ussing ssh log-in but not using the command line.

---

### Post by amac777 on 2010-09-01
If VNC does what you need, you may consider tunneling VNC through an SSH connection over the internet. I belive there are many tutorials on doing this including some on these forums. For example: 

[http://ubuntuforums.org/showthread.php?t=1548097&highlight=tunnel+ssh+vnc](http://ubuntuforums.org/showthread.php?t=1548097&highlight=tunnel+ssh+vnc)

---


---
title: "Remote Control"
date: 2011-09-27
forum: General Help
---

### Post by absentcrisis on 2011-09-27
I am trying to get more familiar with ubuntu and use it more in my every day tasks. I am having problems using ubuntus remote control tool to get control of my windows desktops. I use VNC to try and get in does vnc need to be installed on all clients to get this to work? if so is there a better remote tool for ubuntu?

Thanks

---

### Post by absentcrisis on 2011-09-27
Answered my own question....lol Remmia Remote desktop client has an option for RDP and it works flawlessly.

---

### Post by seawolf167 on 2011-09-27
You need a [VNC]("https://help.ubuntu.com/community/VNC") [server]("https://help.ubuntu.com/community/VNC/Servers") on the computer you are connecting to, and a [viewer]("https://help.ubuntu.com/community/VNC/Clients") on the machine you are connecting from.

[UltraVNC]("http://www.uvnc.com/"), [TightVNC]("http://www.tightvnc.com/"), etc.

As you discovered you can use RDP programs as well as SSH servers on windows (like [freeSSHD]("http://www.freesshd.com/")) then connect via [SSH]("https://help.ubuntu.com/community/SSH")

---


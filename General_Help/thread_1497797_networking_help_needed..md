---
title: "networking help needed."
date: 2010-05-31
forum: General Help
---

### Post by manji_kun on 2010-05-31
Okay, so i had the idea of transferring some of my video's and pic's from my laptop which has windows 7 ultimate on it, to my desktop which is running Ubuntu 9.10 (till 10.4 isn't buggy) i allowed access to both computers through a LAN direct cable, direct as in laptop directly to desktop Ethernet connection.

 i gave both accounts access to each other, made a "Homegroup on my laptop and still nothing, can/will anyone explain to me if i did something wrong and how to actually do this?

---

### Post by spiky001 on 2010-05-31
You will need to install Samba on Ubuntu machine to share with windows

---

### Post by manji_kun on 2010-05-31
ok, i installed samba-doc and samba-common through synaptic, what's next? =D

---

### Post by spiky001 on 2010-05-31
Have a read through this

should solve the problem [http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

---

### Post by akakingess on 2010-05-31
Now you should be able to go to the "Places" menu and choose network and find that computer, or if you know the Windows machine's IP address, you can actually go to Firefox (for example) and in the address bar type smb://ip.add.r.ess/ and connect via the browser to the windows box. Also, if you have a folder already shared on the windows box, you could do smb://ip.add.r.ess/nameofsharedfolder and go directly to that directory. That's just a couple of ways to try to connect 'em. Let us know whether those work or not.

---

### Post by fclm on 2010-05-31
maybe u need to turn off the firewall? 
**[COLOR=#444444][FONT=Verdana][SIZE=3][/SIZE][/FONT][/COLOR]**

---


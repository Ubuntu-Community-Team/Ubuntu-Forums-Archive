---
title: "connecting 2 pcs?"
date: 2011-03-30
forum: General Help
---

### Post by rahulbest on 2011-03-30
i have one laptop and desktop....i connected both of them to one router....now i want to share and access files of desktop from laptop how i can do that???

---

### Post by papibe on 2011-03-30
Do they both have Linux on it?

Regards.

---

### Post by collisionystm on 2011-03-30
2 ubuntu machines? or is windows involved

---

### Post by rahulbest on 2011-03-30
both have ubuntu 10.10

---

### Post by papibe on 2011-03-30
Then the best option is nfs . Here are some tutorials:

[From the help.ubuntu.com]("https://help.ubuntu.com/8.04/serverguide/C/network-file-system.html").
[From the forums]("http://ubuntuforums.org/showthread.php?t=249889").

Regards.

---

### Post by collisionystm on 2011-03-30
The easiest way for you is probably to Just make a folder on your computer, right click on it and go to sharing. share the folder and allow guest access. open terminal, type ifconfig, find the ip address for eth0 or wlan0 or eth1 whatever it is, and on the other ubuntu go to places, browse to server, select windows share, and put in the ip of linux box you grabbed the ip from.

If you dont like this method, read about ssh and rsync and stuff like that. I am just trying to be simple

---


---
title: "Force scanning of wifi networks after suspend"
date: 2010-12-31
forum: General Help
---

### Post by squenson on 2010-12-31
Hi all,

After I put my laptop in suspend mode and I resume it, it doesn't immediately detect the wifi networks. I have to wait for 5-10 minutes to see the various networks appearing.

Is there a command I could run from the terminal to scan the wifi networks? I have tried the wcid application but I got some kind of conflict and then I removed it.

Thanks in advance for your help!

---

### Post by hakermania on 2010-12-31
Restarting the Wifi by hand doesn't solve the problem?

---

### Post by squenson on 2010-12-31
Switching the wifi button off and on doesn't help. I still have to wait 5-10 minutes.

---

### Post by hakermania on 2010-12-31
```
sudo /etc/init.d/network-manager restart
```
seems to work a bit for me :)

---

### Post by squenson on 2010-12-31
It seems to work, thank you! I also got a message telling me that the command "restart network-manager" is another possibility.

I will test and let you know.

. . . .

The command:
sudo /etc/init.d/network-manager restart

is working very well. Thank you hakermania!

---

### Post by hakermania on 2011-01-01
You're welcome, mark the thread as [Solved] please and a note: If you want to just click your panel and run the command (not to open every time a terminal to run this command) you can use gksudo instead of sudo :)

---


---
title: "how to set up dial-up access to the Internet"
date: 2009-07-20
forum: General Help
---

### Post by dluzius on 2009-07-20
I made an extra Ubuntu live CD and gave it to a friend, He installed Ubuntu on his laptop, but can't figure a way to set up an Internet connection to the Internet. He only has access to the Internet using a dial up connection. Can someone please take me step by step through the process, so I can help him with this. TIA     Dave

---

### Post by michy99 on 2009-07-20
Hopefully, this can help:

 [Dialup Modem Howto]("https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer")

---

### Post by t4thfavor on 2009-07-20
Hopefuly he has access to a real hardware based modem, as softmodems make it very difficult to use. If he only has the internal modem on his laptop, look into slmodemd..


Good luck.

---

### Post by bammers on 2009-07-26
Hi there - I hope someone can help.  I have succeeded in getting a dialup connection working with gnome-ppp, which is fine.  Now I want to take it to the next stage which is to make it the default connection to the internet (no broadband).  This means if I use any networking application (firefox, thunderbird, telnet, ssh, ping, etc), I want either wvdial or gnome-ppp to be started automatically.  I know it can be done, just can't figure out what the recipe is!
Can anyone help?
Details:

$ cat /etc/issue
Ubuntu 9.04 \n \l


$ cat /proc/version
Linux version 2.6.28-13-generic (buildd@vernadsky) (gcc version 4.3.3 (Ubuntu 4.3.3-5ubuntu4) ) #45-Ubuntu SMP Tue Jun 30 19:49:51 UTC 2009

gnome-ppp version: 0.3.23-1

Let me know if you need any more info!

Thanks,

- bammers

---


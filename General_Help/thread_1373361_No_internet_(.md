---
title: "No internet :("
date: 2010-01-05
forum: General Help
---

### Post by smiich on 2010-01-05
Hi im new to ubuntu, just installed it a few hours a go. I've managed to get it hooked up to my wireless connection but still the internet doesnt work. Any tips on what i can do to get it working?

Thanks

---

### Post by SanjogS on 2010-01-05
Ive got the same problem, it worked at first, but it isn't working today, and the notification area got crazy.

---

### Post by khelben1979 on 2010-01-05
Take a look in **/etc/init.d/** and take a look at the starting scripts which you have in there (the path might differ from my Debian system, but should not differ too much).

In my system I have a script which is called: networking which uses [DHCP]("http://en.wikipedia.org/wiki/Dhcp") to find an IP address with my [ISP]("http://en.wikipedia.org/wiki/Internet_Service_Provider").

I do the following:
```
cd /etc/init.d/
sudo ./networking restart
```
Then you wait until it reports that it has found an IP address which the system can use.

It might be that your system is using a network time out which cuts you off from your internet connection, or.. there could be something else.

---

### Post by bkratz on 2010-01-05
Another interesting DHCP thread

[http://ubuntuforums.org/showthread.php?t=1156441](http://ubuntuforums.org/showthread.php?t=1156441)

---

### Post by smiich on 2010-01-13
Thanks, this problem fixed itself in the end. Sometimes it connects, sometimes it doesnt.

---


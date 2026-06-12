---
title: "install bcm4312"
date: 2012-01-29
forum: General Help
---

### Post by omar2542012 on 2012-01-29
hi. im new here,and i realy need help. first sorry for my bad english. i have a laptop hp pavilion g6 with backtrack 5 r1 gnome 32 bits i want to install driver of my wireless card &quot;broadcom 4312&quot; i tried a lot of subject and tuts,but without any result. here is some subjects: [http://forum.backtrack-fr.net/viewtopic.php?id=4119](http://forum.backtrack-fr.net/viewtopic.php?id=4119) [http://www.debian-fr.org/comment-instal](http://www.debian-fr.org/comment-instal) … 34728.html  the result of iwconfig:  ```
 lo        no wireless extensions.  eth0      no wireless extensions. 
```

---

### Post by Wayne_V on 2012-01-29
I would start here:

[http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)

---

### Post by grahammechanical on 2012-01-29
We try to be helpful here at Ubuntu Community Forums.

Backtrack is a specialized operating system. It is based upon Ubuntu but it is not compatible with Ubuntu. We may not be able to help you because we may not be familiar with the Backtrack user interface and system utilities.

I give you this:

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide")

Use the commands to examine your system and use the commands to try to fix the problem.

I also give you this from the Backtrack Frequently Asked Questions (FAQ)

[http://www.backtrack-linux.org/wiki/index.php/FAQ]("http://www.backtrack-linux.org/wiki/index.php/FAQ")

Please note this:

> **Why don&#8217;t my network cards show up when I boot ?**

> BackTrack is a penetration testing distribution and as such DHCP requests etc entering the network when you boot are usually very undesirable. You can easily enable networking by issuing the following command:

```
/etc/init.d/networking start
```

Regards.

---


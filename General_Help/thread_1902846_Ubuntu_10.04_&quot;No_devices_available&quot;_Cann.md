---
title: "Ubuntu 10.04 &quot;No devices available&quot; Cannot connect to internet."
date: 2011-12-31
forum: General Help
---

### Post by KebertX on 2011-12-31
Fresh install. Network setup won't work for whatever reason. It didn't recognize the wireless card, and without internet I cannot install drivers or anything.

```
/etc/network/interfaces
```
Is as follows:
```
auto lo
iface lo inet loopback
```
No wlan0 or eth0. If I just write some things in, it returns an error when I run /etc/init.t/networking restart.

[http://ubuntuforums.org/showthread.php?t=1594566](http://ubuntuforums.org/showthread.php?t=1594566)
That thead did me no good...
[https://help.ubuntu.com/8.04/printing/C/scanning.html](https://help.ubuntu.com/8.04/printing/C/scanning.html)
Nor did this...

Just give me some tips, I don't know what to do.

---

### Post by 3rdalbum on 2011-12-31
> **KebertX said:**
> Fresh install. Network setup won't work for whatever reason. It didn't recognize the wireless card, and without internet I cannot install drivers or anything.

```
/etc/network/interfaces
```
Is as follows:
```
auto lo
iface lo inet loopback
```
No wlan0 or eth0. If I just write some things in, it returns an error when I run /etc/init.t/networking restart.

[http://ubuntuforums.org/showthread.php?t=1594566](http://ubuntuforums.org/showthread.php?t=1594566)
That thead did me no good...
[https://help.ubuntu.com/8.04/printing/C/scanning.html](https://help.ubuntu.com/8.04/printing/C/scanning.html)
Nor did this...

Just give me some tips, I don't know what to do.

Ubuntu 10.04 is ancient. Try 11.10 as it has more wireless drivers, and more recent ones. Also, don't follow instructions from old versions of Ubuntu as they are unlikely to work. Especially 4-year-old instructions.

---

### Post by KebertX on 2011-12-31
I went back in time to 10.04 as a way of rebelling against the Unity desktop. I dislike it. I know I can get rid of it in synaptic, but I'd rather Lucid Lynx would just work. And it does. But I really need to know how to connect it to the internet. If absolutely no solution exists, I'll try Natty out.
But where there's a Shell, there's a way! So can anyone help me out?

---

### Post by vpharry on 2012-01-01
Try if the wireless card gets recognised in windows... it may be a problem with the card(which is unlikely) or contact the card manufacturer with your problem... and you should seriously move onto oneiric...  theres a classic gnome option too or shift to xubuntu or lubuntu or something...

---

### Post by KebertX on 2012-01-01
I had Oneric on my other computer, and after 2 months I just switched to gentoo. I can't explain why, it just annoyed me.

Sorry guys, I'm a purist, I'm not going later than 10.10 on this computer. I  can find the right drivers on my own, I suppose. If I just Identify the wireless card, then download the .deb package for that driver, and save it to a flash drive and dpkg it, I think I'll be okay. Any objections?

Maybe I'll move up when 12.X comes out. Maybe.

Maybe.

---

### Post by noletolucas on 2012-03-17
I have a Dell Inspiron with Wifi Card "Atheros AR8152 PCI-E Fast Ethernet Controller" and I have the same problem: no devies detected.

Tried Ubuntu 10.04. Works just fine with Win7 (default OS from factory)

---

### Post by killminus9 on 2012-04-01
I have a Dell Inspiron 14z-N411z laptop with an Atheros Communications Inc. AR8152 v2.0 Fast Ethernet NIC.  During the install of Ubuntu 10.04.3 LTS the NIC is not detected, as described previously.  I've tried the fix posted here [http://ubuntuforums.org/showthread.php?t=1505697&highlight=Atheros+AR8152]("http://ubuntuforums.org/showthread.php?t=1505697&highlight=Atheros+AR8152") but I guess since the fix is for v1.1 I shouldn't be surprised it didn't work for me, but maybe it will work for someone else.

Is anyone aware of a driver available for v.2.0?

I am unable to "upgrade" to Ubuntu 11.10 due to a bug that currently does not allow for virtual NIC interfaces.

thank you!

---


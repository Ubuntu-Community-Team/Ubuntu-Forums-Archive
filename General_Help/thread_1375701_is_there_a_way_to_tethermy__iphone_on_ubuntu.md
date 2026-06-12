---
title: "is there a way to tethermy  iphone on ubuntu?"
date: 2010-01-08
forum: General Help
---

### Post by BAleR187 on 2010-01-08
Now on windows 7 of course, i just turn on tethering on my phone, plug it in and windows installs the drivers for my phone via usb. Does anyone know where I can get drivers for this on ubuntu? or just know a way to set this up? any help is greatly appreciated thanks

---

### Post by Zorael on 2010-01-08
Supposedly yes, if it's jailbroken.

It's now possible to connect to iPhones and Touches over USB (even non-jailbroken ones) if you follow the procedures detailed in [this thread](http://ubuntuforums.org/showthread.php?t=1355610), but you need to have an SSH server installed on the device to be able to set up tethering. I haven't tried it myself, but as per [this post](http://ubuntuforums.org/showthread.php?p=8555588);
> **Mandor_ said:**
> Interesting note: if you happen to have an iPhone that's jailbreaked and has OpenSSH installed, you can use this guide to tether the iPhone's internet connection. The usbmuxd package (which gets installed along with iFuse) comes with a nifty utility called iproxy that allows you to create a tunnel to the device:
```
iproxy 2222 22 &
```This creates a tunnel from port 2222 to the port your iPhone's OpenSSH listens on by default.
Next use SSH to create a SOCKS proxy to the tunnel:
```
ssh -D 1080 -p 2222 root@localhost
```Now all you have left to do is to set Firefox's proxy settings: SOCKS v5 proxy on host 127.0.0.1 and port 1080.
Also in about:config, set *network.proxy.socks_remote_dns* to true. Voilà!

---

### Post by nicoseb on 2010-01-08
I should check that USB method just to see...

Anyway, the other solution is:
- Jailbreak yoru iphone
- Install ROCK
- Intsall MyWi

And there you go... you can tether via wifi!
This works like a charm, as a matter of fact, that is the connection I am using right now!
;)

---

### Post by BAleR187 on 2010-01-08
> **nicoseb said:**
> I should check that USB method just to see...

Anyway, the other solution is:
- Jailbreak yoru iphone
- Install ROCK
- Intsall MyWi

And there you go... you can tether via wifi!
This works like a charm, as a matter of fact, that is the connection I am using right now!
;)


yes that is a very effective way to do it, the only problem with that is, I have a D-Link usb wireless adapter that I cant seem to get to work on ubuntu, I cant find any drivers for it??

---

### Post by BAleR187 on 2010-01-08
> **Zorael said:**
> Supposedly yes, if it's jailbroken.

It's now possible to connect to iPhones and Touches over USB (even non-jailbroken ones) if you follow the procedures detailed in [this thread]("http://ubuntuforums.org/showthread.php?t=1355610"), but you need to have an SSH server installed on the device to be able to set up tethering. I haven't tried it myself, but as per [this post]("http://ubuntuforums.org/showthread.php?p=8555588");



Thanks Z, i will give it a shot, and yes mine is jb, and have ssh installed, never used it though, but thanks for the help man:D

---


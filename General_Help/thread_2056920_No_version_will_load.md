---
title: "No version will load"
date: 2012-09-12
forum: General Help
---

### Post by Humph7ey on 2012-09-12
First post.):P
I have tried versions 9 to 12 but none will load. I wiped the HD with Darik's boot and Nuke before trying as the original XL was corrupted.
In the earlier versions, the orange dots stop and the caps lock light blink. 
I have a c 2003 Toshiba laptop PSM35E with Intel and 40G hd. 
Is there any program that will prepare it for loading Linux?
I hope someone can help as I have wasted days on this so far.
Humphrey

---

### Post by steeldriver on 2012-09-12
On a machine of that vintage I would try something like Xubuntu, using the 'alternate' iso

[http://xubuntu.org/getxubuntu/](http://xubuntu.org/getxubuntu/)

I have that running on a PIII-M Thinkpad (albeit with 1GB RAM - if you have less RAM you might want to look at something even lighter)

---

### Post by Humph7ey on 2012-09-12
I believe it has 768 MB of RAM (according to Mini XL)
It's now installing the base system.
Failed attempt "the target file system contains files from a previous installation.
It won't allow me to go further so I will abort.
Tomorrow I will try an earlier version.
Odd, as I had cleaned the hard drive.

---

### Post by opensshd on 2012-09-12
Yes, odd.

Have you tried loading any of these versions or just installing? Have you tried loading the live OS from the installation disk?

Sounds like you need to reformat that disk. I would try doing that with gparted from a Ubuntu live OS.

---

### Post by varunendra on 2012-09-13
Welcome to the forums Humph7ey !

> **steeldriver said:**
> if you have less RAM you might want to look at something even lighter)
- perhaps [Lubuntu]("http://lubuntu.net/") ??
I would use [torrent]("http://cdimage.ubuntu.com/lubuntu/releases/12.04/release/lubuntu-12.04-desktop-i386.iso.torrent")  to ensure integrity of the downloaded iso.

I have successfully used mint9-lxde on an eight year old compaq notebook with 768MB RAM (originally it had just 256MB RAM). But mind you - I also used two 'virtual machines' (one DSL with 64MB RAM allocation, the other 'Win server 2003' with 128MB RAM allocation) simultaneously on it, which means, there was less than 576MB RAM available to mint when running those VMs, and it still ran smoothly ! :)

However, if your laptop can't handle the GUI of the live cd, install using alternate disc as *steeldriver* suggested. Here are the links (from [https://help.ubuntu.com/community/Lubuntu/Alternate_ISO](https://help.ubuntu.com/community/Lubuntu/Alternate_ISO)) :
Torrent : [http://cdimages.ubuntu.com/lubuntu/releases/precise/release/lubuntu-12.04-alternate-i386.iso.torrent](http://cdimages.ubuntu.com/lubuntu/releases/precise/release/lubuntu-12.04-alternate-i386.iso.torrent)
Direct download : [http://cdimages.ubuntu.com/lubuntu/releases/precise/release/lubuntu-12.04-alternate-i386.iso](http://cdimages.ubuntu.com/lubuntu/releases/precise/release/lubuntu-12.04-alternate-i386.iso)

---

### Post by Humph7ey on 2012-09-13
I just ran a diagnostics and it states that S.M.A.R.T. has detected a problem and the hdd will fail and should be replaced asap.
Could it be why the Win XL that was on there was totally corrupted?

---

### Post by varunendra on 2012-09-13
> **Humph7ey said:**
> I just ran a diagnostics and it states that S.M.A.R.T. has detected a problem and the hdd will fail and should be replaced asap.
Could it be why the Win XL that was on there was totally corrupted?
Most probably.
Immediately backup your importnt data on an external drive using the live cd if you can. Use another hard disk for your OS (for Ubuntu, you can even use a usb flash drive). As for the current one, you can still keep using it (until it eventually dies) as a storage drive for non-important data (but that will certainly hinder the performance if the disk is really failing..).

---

### Post by Humph7ey on 2012-09-13
I just ordered a replacement HDD. Thanks for all your help.:KS
I may revive this thread if I still have the same trouble.

---

### Post by Humph7ey on 2012-09-17
I loaded Xubuntu 12.04 Now it won't make an internet connection. It does allow the play of cds, which Windows did not allow.

---

### Post by varunendra on 2012-09-17
> **Humph7ey said:**
> I loaded Xubuntu 12.04 Now it won't make an internet connection..Start a new thread for that, since it is a different issue. If it is the wireless interface, download and run 'wireless_script' from the link in my signature, and post back the contents (in your new thread) of the 'netinfo.txt' file it creates. Then post back a link to that thread here so we can follow.

As for this one, if you think the prob. is solved, please mark it as such (see my sig. to see how).

---


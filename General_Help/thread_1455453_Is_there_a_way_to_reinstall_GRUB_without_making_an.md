---
title: "Is there a way to reinstall GRUB without making another Ubuntu flash drive?"
date: 2010-04-16
forum: General Help
---

### Post by ilikedginger on 2010-04-16
I have a Gateway Netbook with Ubuntu Netbook Remix installed.

I recently had to restore Windows 7 and while GRUB worked immediately after, a restart later, for some reason now all that happens is "GRUB Loading..." and then the computer immediately restarts itself. And that continues until I manually turn it off/throw it against the wall.

I've been looking around and I have seen others who had this problem reinstalled GRUB off their original live disk, but I don't have a CD Drive and the original flash drive is... well, I have no idea where that is, I'm pretty sure my boyfriend cleared it and put something else on there.

Is there a way to fix this without making another bootable flash drive?

I've read tutorials on how to install GRUB itself onto a flash drive, but the instructions were linux based and I'm stuck on windows right now.

---

### Post by uRock on 2010-04-16
If Windows will run, then you can download and install [unetbootin]("http://unetbootin.sourceforge.net/") and use it to get ubuntu reinstalled.

---

### Post by ilikedginger on 2010-04-16
> **uRock said:**
> If Windows will run, then you can download and install [unetbootin]("http://unetbootin.sourceforge.net/") and use it to get ubuntu reinstalled.

Unfortunately, nothing will run on the computer in question. I'm on a different computer right now.

I know I can make another flash drive/ubuntu installation, I was just hoping there was a way to fix GRUB without having to make a new Ubuntu Installation "CD".

---

### Post by uRock on 2010-04-16
> **ilikedginger said:**
> Unfortunately, nothing will run on the computer in question. I'm on a different computer right now.

I know I can make another flash drive/ubuntu installation, I was just hoping there was a way to fix GRUB without having to make a new Ubuntu Installation "CD".
If you know of someone with an external CD drive you could easily run the LiveCD. That is how I install to my Netbook.

---

### Post by ilikedginger on 2010-04-16
Yeah, don't know anyone who would know what that was.

It's weird too, because I finally broke down and just downloaded the UNR iso and was trying to use Universal USB to make a bootable flash drive and it's giving me errors.

Kind of a bummer, because I ended up barely ever getting to use Ubuntu in the first place because the wifi didn't work very well with my particular netbook for some reason.

---

### Post by uRock on 2010-04-16
> **ilikedginger said:**
> Yeah, don't know anyone who would know what that was.

It's weird too, because I finally broke down and just downloaded the UNR iso and was trying to use Universal USB to make a bootable flash drive and it's giving me errors.

Kind of a bummer, because I ended up barely ever getting to use Ubuntu in the first place because the wifi didn't work very well with my particular netbook for some reason.

If you get it reinstalled,
> **uRock said:**
> Entering the following code into a terminal fixed  my problem.```
sudo apt-get install linux-backports-modules-karmic
```I found the fix here [https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks](https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks)

---

### Post by ilikedginger on 2010-04-16
Awesome, I'll give it a shot and see how it goes!

Thanks!

---


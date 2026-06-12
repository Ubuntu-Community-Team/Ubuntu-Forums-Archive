---
title: "Ubuntu boot problems"
date: 2010-09-11
forum: General Help
---

### Post by hansihe on 2010-09-11
Hi!

Im having big trouble installing Ubuntu Server/Desktop on my a few years old HP a1509.no.

First when i installed Ubuntu Server(Full hard drive install no resizing) i got "[       7.790675] nForce2_smbus 0000:00:0a.1: Error probing SMB1".
I tried reinstalling several times, disconnecting all usb devices(internal too), booting with "acpi_enforce_resources=lax" and other options.
I also tried installing Xubuntu but the livecd wont boot.

Any ideas what im doing wrong/is going wrong?

Edit:
Its stuck, wont boot if left for a time either

---

### Post by johngreth on 2010-09-11
nForce2 is your graphics card so that may be the problem. Do you have another that you can swap out and try?

---

### Post by hansihe on 2010-09-12
Nope, i dont have another screen card.

By the way the nforce error is said to be usb or or power control related

---

### Post by hansihe on 2010-09-12
Bumpedy bump

---

### Post by johngreth on 2010-09-12
I'm stumped. I cant think of anything that is fixable that usb or power control related that has to do with this. The only other thing that is a long shot is if you are connected to the Internet. I only thought of this because the error says SMB1 somewhere. Otherwise I have no idea. Maybe you could check on the support website to see if your hardware is supported by Ubuntu.

---

### Post by hansihe on 2010-09-12
The wired thing is that i had ubuntu on it before. The only hardware difference is a 1gb ram module that i have tried to remove. Doesnt work when i take it out either.

---

### Post by hansihe on 2010-09-12
Bump!

---

### Post by hansihe on 2010-09-13
Bump!! I really need help!

---

### Post by hansihe on 2010-09-16
Bump!

---

### Post by Rubi1200 on 2010-09-16
Could you post the full specifications, RAM, graphics card etc. please?

Also, did you try burning the .iso at the lowest possible speed?

---

### Post by hansihe on 2010-09-17
> **Rubi1200 said:**
> Could you post the full specifications, RAM, graphics card etc. please?

Also, did you try burning the .iso at the lowest possible speed?

Full specs are [here]("http://h10025.www1.hp.com/ewfrf/wc/document?lc=en&dlc=en&cc=us&lang=en&docname=c00715321&product=3222518")

I will try burning at low speed right now

Edit: Im burning from a mac if that has anything to do with it.

---

### Post by Rubi1200 on 2010-09-17
Also, before burning check the MD5SUM to  make sure there are no problems:
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by hansihe on 2010-09-17
> **Rubi1200 said:**
> Also, before burning check the MD5SUM to  make sure there are no problems:
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

MD5 Checked OK

---

### Post by Rubi1200 on 2010-09-17
> **hansihe said:**
> Full specs are [here]("http://h10025.www1.hp.com/ewfrf/wc/document?lc=en&dlc=en&cc=us&lang=en&docname=c00715321&product=3222518")

I will try burning at low speed right now

Edit: Im burning from a mac if that has anything to do with it.

Never used Mac, so I don't know but I wouldn't think it should make any difference.

---

### Post by hansihe on 2010-09-17
> **Rubi1200 said:**
> Never used Mac, so I don't know but I wouldn't think it should make any difference.

Im following the official instructions so, i guess it is ok.

---

### Post by Hero_Lief on 2010-10-19
I understand that this thread is little over a month old, however I'm getting this problem too. I've used Ubuntu for years on my machine, with multiple installs, dating back to 9.04. Recently, 10.04 has given me errors at boot; 10.04 worked fine for months, but in the past month or so these errors have popped up. I boot the machine, BIOS loads, and Ubuntu begins to boot. I get the splash screen, and then it freezes. So I reboot. As soon as it gets to the splash screen, I hit ctrlaltf1 to see if there are any error messages. It loads for about ten seconds, then displays "nForce2_smbus 0000:00:0a.1: Error probing SMB1.". It freezes from there. Upon searching, there are multiple bugs scattered around, namely [this one](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/440470), however it mentions listing a parameter in grub2 for the kernal. I don't even have GRUB installed; ever since I wiped Windows off of my drive, GRUB is gone as well, so it simply boots into Ubuntu. Also, some suggested that my hardware may be to blame. I have a dual-core 64-bit Athlon 3800+, GeForce 9400GT, and I'm not sure of my network card, but besides my 2GB of RAM and my GeForce, everything is the default of the way my computer came 5 years ago from HP (It's an a1430n Pavilion) The strange thing is, that I plugged in a Windows (XP Media Center Edition 2005) drive, unplugging my Ubuntu one, and attempted to boot from that; Along with having to deal with terrible speeds and installing new drivers for the different hardware specs, it works perfectly fine, leading me to believe that my hardware isn't to blame. So, any troubleshooting I can do or other things I should try? I'd prefer to get this system operational again; not to wipe over it.

---

### Post by LeoMunky on 2011-05-07
Just fyi, nforce is a motherboard chipset, not graphics. geforce is the graphics.

---


---
title: "very basic boot cd"
date: 2010-09-06
forum: General Help
---

### Post by hodgestructure on 2010-09-06
I would like to have a bootable CD such that after booting, it shows command-line, than I can use fdisk to create, modify, delete partitions. Of course I can use ubuntu livedvd, but I want a very minimal cd with command-line and working fdisk. I have tried minimal install cd, but after booting, it ask too much information for the install environment. Is it possible to create such a boot cd?

---

### Post by hodgestructure on 2010-09-06
OK, I see Ubuntu Mini Remix, 158MB, I will try it

---

### Post by MooPi on 2010-09-06
Would you have any problem using a usb key instead. You can use your minimal install CD to create a command line boot drive. I have something similar that uses a basic Openbox system.

---

### Post by egalvan on 2010-09-06
PartedMagic LiveCD. It has a full GUI, but can certainly run from the command line.

It has a full suite of partition, format and rescue apps.
I've used it for over two years.
I have a subscription donation to it.

[http://partedmagic.com/](http://partedmagic.com/)


Yes, it's more than you asked for,
but it's only 130meg ISO

---

### Post by linux18 on 2010-09-06
the mini iso has such a system (afaik), just perss ctrl+f2 when you run the installerand it will take you to a prompt, best of all it's just 13MB

---

### Post by hodgestructure on 2010-09-06
I think it works on USB. But I prefer to use grub4dos to boot different many bootable iso files.

I tried Ubuntu Mini Remix, it's good. But I just have a litte question. When I tried to use "mkntfs" to format a partition with NTFS type, it said mkntfs is not installed. Of course I could still download and install it, but I don't want to do this everytime I need to use mkntfs (after reboot). So how could I modify Ubuntu Mini Remix CD to include mkntfs?

---

### Post by linux18 on 2010-09-06
just grab the [u]deb and put it on the same disk unless you want to get creative and try reworking it

---

### Post by hodgestructure on 2010-09-07
> **linux18 said:**
> just grab the [u]deb and put it on the same disk unless you want to get creative and try reworking it

Hi, thanks. But I still have some question. I have download 

ntfsprogs_2.0.0-1ubuntu4_i386.deb 

and 

libntfs10_2.0.0-1ubuntu4_i386

and put them in the 

(cd of ubuntu-mini-remix-10.04.1-i386)/pool/main

and make a new bootable cd.

After booting, when I use the command mkntfs, it still said it's not installed. Please type apt-get install ntfsprogs to install it.

How could I modify this CD to make the mkntfs works? Thanks

---

### Post by niteshifter on 2010-09-07
Hi,

Have a look at System Rescue CD, [web site here]("http://www.sysresccd.org/Main_Page").

---


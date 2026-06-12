---
title: "Want to install windows 7"
date: 2011-08-02
forum: General Help
---

### Post by ltwinner on 2011-08-02
I dual boot ubuntu with windows xp using grub. I need to install windows 7 now too. How do I go about doing this?

---

### Post by raja.genupula on 2011-08-02
Man you can do it .but windows bootloader may be override the grub . it doesnt sounds much safe . again you have to configure your grub .

---

### Post by Frogs Hair on 2011-08-02
Here is a place to start , check the Windows after Ubuntu section . I have not attempted a triple boot , so I can't help . [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by cogier on 2011-08-02
Windows will not see any other operating system - do not try to install Windows 7 over XP it will wipe Ubuntu. 

You will need to install Windows first and then Ubuntu.

You could run Windows 7 in Virtualbox!

---

### Post by nickleboyblue on 2011-08-02
Step 1: make sure you have three partitions, each formated to the correct format for each operating system you will be using.

step 2: install windows seven on it's partition.

step 3: install windows XP in it's partition.

step 4: install Ubuntu on it's partition.

Once this is done, grub should be able to recognize the other operating systems and allow you to choose between them.

I have not done this with a tri-boot setup, but I have with dual boot.  Personally, I don't see any reason to do a tri-boot unless there is XP-specific software you absolutely need.  Tri-booting takes up a lot of hard drive space and is very difficult to pull off.  Just make sure you have all of your data backs up and that you have a backup plan in case this one fails.

Again, I strongly suggest that you only dual boot with windows 7, as most software you will be needing now days will be supported by that platform.  Otherwise, figure out how to live inside of Ubuntu alone.  You won't have much by way of proprietary support, but it has done me just fine for several years now.

---

### Post by WorMzy on 2011-08-02
There's no need to reinstall Ubuntu, unless your partitions are in such a mess that you need to start over from scratch in order to set them up properly.

If you have the space, and a free primary partition (or a large enough extended partition with enough space for another partition inside it), then installing another OS is easy enough. The only thing you need to do after completing the installation, is reinstalling grub to the MBR, and updating it so that it can boot to the new OS. There are plenty of guides on how to do that, just make sure you follow one written for Grub 2, not Grub Legacy (since the former is what Ubuntu uses by default).

---

### Post by ltwinner on 2011-08-02
Ok thanks for the info, looks like it is not as simple as I was hoping. I  was hoping I could just create a new partition, stick windows 7 on it  and that would be it.

---

### Post by Jerry N on 2011-08-02
> **nickleboyblue said:**
> Tri-booting takes up a lot of hard drive space and is very difficult to pull off. 

Not a bit more difficult than dual boot.  My test computer currently has 5 OS's on 2 HDs.

---

### Post by WorMzy on 2011-08-02
> **Jerry N said:**
> Not a bit more difficult than dual boot.  My test computer currently has 5 OS's on 2 HDs.

Agreed. I have nine OSes on one HDD. Two Windows, three Ubuntus, four Arches.

Of course, they do take up space, but when you have 3.25 terabytes of HD space, that stops being a concern.

---

### Post by oldfred on 2011-08-02
It is best if you have a primary partition to install win7 into. The standard install will move the boot files from 7 to XP as it is the boot partition. It will work if 7 is in a logical partition but if you ever delete XP you will not be able to boot 7 as it will not have any boot files.

To get each MS to have its own boot loader make a second primary NTFS partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)
Another user who disconnected and used a second drive 
[http://ubuntuforums.org/showthread.php?t=1334346](http://ubuntuforums.org/showthread.php?t=1334346)

---


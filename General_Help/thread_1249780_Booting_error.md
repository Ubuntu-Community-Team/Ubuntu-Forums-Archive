---
title: "Booting error?"
date: 2009-08-25
forum: General Help
---

### Post by -Seven- on 2009-08-25
Hi, I've never used any linux OS before, I just installed it. Upon rebooting after complete installation, (I installed it as a dual boot with windows 7rc) I selected ubuntu from the OS selection screen, and then I get a black screen with this text:
 
Try (hd0,0): NTFS5: No wubildr
Try (hd0,0): Extended
Try (hd0,0): invalid or null
Try (hd0,0): invalid or null
Try (hd0,0): EXT2:_

From here it proceeds to do  nothing but stay on this screen. 

I've googled this problem and only found a page that didn't give me much help, I'm not sure it was even the exact same problem....so here I am.
 
I worked on figuring out how to remove ubuntu but it turned out to be a nightmare so I gave up and am now trying to solve this problem. The partition in gparted won't even show up correctly (I can go check for what exactly it shows if you'd like, {not at home}) so I can't even tell what to delete.
 
Just remember that I'm a nub with this OS. I'd be glad if anyone would be willing to recommend some great starter guides, I want to learn this OS inside and out. I'm gonna be working with network security (and cracking, for fun) on it.
 
Muchly appreciated. Peace :)

---

### Post by P4man on 2009-08-26
You tried a wubi install? (from inside windows) or did you boot of the cd and install from there?

---

### Post by -Seven- on 2009-08-26
Well, actually I used the wubi installer that was included in the live cd disk, I installed it on windows, I rebooted the computer, when I came back to my computer I saw an install icon on the GUI and figured I should just go from there and installed it again. With the wubi install though it had non of the configuration options, such as language and keyboard layout. 

Though yesterday I found that it never actually installed on the HDD I had selected, so I deleted all the partitions of it off that HDD and tried to reinstall it correctly, but I found when it got to the partition editor in the installation, it wouldn't recognize my Windows 7 OS on my new HDD, but would only recognize my old Windows XP OS on a separate harddrive. It wouldn't do anything when I selected the proper HDD. When I use Gparted on the live cd (not in installation) it shows my Windows 7 HDD as unnalocated. It is recognized in the wubi installer but I'm not sure if I should proceed with that. Thanks

---

### Post by P4man on 2009-08-26
ubuntu doesnt play nice with windows 7 yet apparently. Normally, the installer would recognize the windows partitions and install a bootloader that lets you dualboot. With windows 7, apparently it can not (yet). 

But there is a solution. You can use the winows 7 bootloader to boot linux.

What you should do, is boot from the live cd. Install to the correct partition (and thank god you noticed the windows 7 partition was what it was, and not "unallocated"!!). At the end of the installation process there is an advanced button:

[IMG]http://www.davescomputertips.com/images/newsletter/2008/20080615/installation_7.png[/IMG]

**Dont miss it!**

There it asks you where to install the grub (ubuntu) bootloader. By default it will probably want to install on the first partition of the first harddisk (windows 7 I suppose). Change that. Either dont make it install a bootloader at all, or make it install on the ubuntu drive if its a seperate drive. If you are unsure of the names of the drives, post here before letting it start!

If you chose the latter approach, then you can use your bios boot menu to boot ubuntu by booting off another disk. If you use either approach, you can later modify windows 7 bootloader to include an option for ubuntu. You can do that with EasyBCD

[http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)

(never used it, but reportedly works well).

---

### Post by -Seven- on 2009-08-26
Oh crap, I forgot to mention that (and I have no idea how it happened, I was a bit spacey) after I unplugged my other HDD's, in hopes that it might force it to recognize the proper one, and rebooted, it tried to use the GRUB loader instead, every instance before this it used the windows boot loader, but with the GRUB loader (and no Ubuntu on my computer) I got an error 22 message, so I'm forced to reach the windows boot loader through the live cd menu ("boot from first hard disk").

But thanks for that info, I'll give it a try.

---

### Post by -Seven- on 2009-08-26
Well, from what I've read, other people have been able to dual boot Windows 7, even beta versions. Could this possibly mean that my HDD could be damaged? Not too long after I got it it was doing some funky stuff where my computer would get rediculously slow, I tested pretty much everything and rooted the problem to most likely be the HDD itself. But it mysteriously fixed itself out of nowhere. Anyway, since I can't select my W7 HDD for dual booting I guess I'll clear out one of my old IDE drives and wait till this bug is fixed, if it is indeed a bug (I hope X_X).

As for your guide, I can't reach step 7 because I can't select the HDD I'd like to install it on.

I appreciate the help. This is confusing X_X.

---

### Post by P4man on 2009-08-26
I just tried hooking up a w7 drive to my main computer.. and (I guess unfortunately for you?), my ubuntu recognizes it just fine and can read/write to it. However, maybe its neither a bug nor a hdd failure, perhaps you are using dynamic disk or something that ubuntu can't read? 

> 
As for your guide, I can't reach step 7 because I can't select the HDD I'd like to install it on.

You can't select it where? Partition editor ? Can you open a terminal (apps > accessories > terminal ) and post the output of

```
sudo fdisk -l
```

---


---
title: "Kunbuntu, BackTrack &amp; Unbuntu + windows 7"
date: 2010-06-19
forum: General Help
---

### Post by teddy101 on 2010-06-19
I have  partitiond my hard drive on one side I run Kubuntu (and when I finish  downloading; Ubuntu) on the other windows 7.
 
However I dont know how to co run (and set-up) so I can swap between KDE  GNOME and how to make Back track (I have on live C.D.) run with bash or  KDE.
 
Cuting this way to long story short, i am hoping one of you amazing  peeps can tell me how to run backtrack, kunbuntu and Ubuntu on the same  side of the hard drive??!!
 
Thanks guys.
 
Tom [IMG]http://www.linuxforums.org/forum/images/smilies/icon_smile.gif[/IMG]

---

### Post by admiralspark on 2010-06-19
Hello Tom,
First off, Backtrack also uses KDE, which is just a desktop environment. It will boot to a bash CLI, and then typing "startx" will start KDE. Anyways,
I'm not sure what you mean by "side" of the harddrive. I assume that you mean it's all on one harddrive, but you have multiple partitions. If this is so, you will need:
*One partition with Win7 on it formatted to NTFS (you have this already)
*three partitions for Kubuntu, Ubuntu and Backtrack respectively.

Now, I'm thinking that you can only have four bootable partitions per harddrive using Grub2 (the bootloader, will get to it in a second). For a simple install, you will want to make three more partitions for the linux distro's, formatted to Ext3. Install Kubuntu first (if windows is already installed), then Backtrack, then Ubuntu. When you're finally done installing everything, grub2 should automatically update it's menu for you. Basically, it will have a menu with Ubuntu at the top, then Kubuntu, then Backtrack (which will be called Ubuntu 8.04 for complicated reasons), then windows 7 at the bottom. 

If this sounds complicated, it's because it is...if you want step-by-step instructions (much more clear than the above) I can give them, but you'll have to let me know first. 

Just so you know, I usually triple boot XP/Ubuntu/Backtrack and use puppy from a Usb, and I've done multiboot setups many times, so I have full faith in this working.

---

### Post by teddy101 on 2010-06-22
Thanks a ton for the help :) I have been so very busy!!

After many an hour of trying I have given up trying to achieve what I after and used GRUB as everyone keeps telling me I Thankyou again for the advice! 

In the end I removed windows it was really and trully to much effot and way to big! :)

---

### Post by admiralspark on 2010-06-22
No problem. One thing: you may sometime want to use windows to run a windows-specific program that Wine doesn't cover (the list of ones that don't work with wine gets smaller every day). If you ever have the need, you can always run Windows inside of Ubuntu using Virtualbox. 

Otherwise, enjoy *buntu!

---


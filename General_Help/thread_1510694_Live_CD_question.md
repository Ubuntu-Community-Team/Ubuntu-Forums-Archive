---
title: "Live CD question"
date: 2010-06-15
forum: General Help
---

### Post by DemonSharkKisame on 2010-06-15
Hey everyone. As a former Ubuntu user (switched back to XP for some personal reasons, though Ubuntu's again an option now that my computer has decent specs), I have a question about the Live CD. Specifically, would downloading and enabling restricted drivers for my graphics card (Nvidia GeForce 4 MX440) affect it in any way if I boot back to Windows or will the drivers reset back to normal? I don't want to damage my system...

---

### Post by Chesamo on 2010-06-15
Drivers installed on Ubuntu will have no effect on your Windows setup. Drivers are software interfaces for the operating system, they should never impact your hardware.

---

### Post by DemonSharkKisame on 2010-06-15
Not even from the live CD? (just want to be sure before I potentially screw anything up/have to reinstall drivers/etc.)

---

### Post by happyhamster on 2010-06-15
If you boot into a live session using a live cd, nothing on your system will be affected (hard-drives aren't even mounted). The live-cd only needs, and only uses RAM and the live-cd itself. The hard-drives are ignored.

---

### Post by Chesamo on 2010-06-15
> **DemonSharkKisame said:**
> Not even from the live CD? (just want to be sure before I potentially screw anything up/have to reinstall drivers/etc.)
You can't enable the restricted drivers on the LiveCD as they require a reboot.

---

### Post by DemonSharkKisame on 2010-06-15
Hm, so I'd have to install Ubuntu in order to actually use the drivers? That stinks... all I have is a 20 GB hard drive, so I don't have the space with the programs and stuff I have installed in XP to dual-boot with Ubuntu...

---

### Post by Chame_Wizard on 2010-06-15
Every OS have drivers modules to work correctly.

---

### Post by ssulaco on 2010-06-15
> **DemonSharkKisame said:**
> Hm, so I'd have to install Ubuntu in order to actually use the drivers? That stinks... all I have is a 20 GB hard drive, so I don't have the space with the programs and stuff I have installed in XP to dual-boot with Ubuntu...
Wubi install is an option...do you have 5 gig to spare?your live cd should have the wubi installer
> 
What are the system requirements?

256 MB RAM and an 1 GHz or faster Intel/AMD processor is recommended for optimal performance, though Xubuntu might work on less. As for disk space, the installation requires a minimum of 5GB free. This space is mostly used by the virtual hard disk file. Most computers purchased within the last 3 years should be able to run Ubuntu fine, and Xubuntu is suitable for older computers. Software raids (aka fakeraid) are not supported. Encrypted disks are not supported.

[http://www.psychocats.net/ubuntu/wubi](http://www.psychocats.net/ubuntu/wubi)

---

### Post by DemonSharkKisame on 2010-06-15
No, I only have just over 2 GB to spare on my main drive... however, a friend of mine might be able to kick me a spare 40 GB drive that I can use alongside my 20 (my computer's got room for up to 3 HDDs if I get rid of my floppy drive), so it's not all bad.
(oh! Just so I don't take up additional forum space, how easy is it to set up a dual-boot between two separate hard drives? Will the Ubuntu installer take care of that or will I have to muck about in GRUB in order to choose between which drive to boot from? I want to see if I might run into any major issues before I install that second hard drive...)

---

### Post by ssulaco on 2010-06-16
great tutorial on dual boot/2 drives....
[http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902)

---


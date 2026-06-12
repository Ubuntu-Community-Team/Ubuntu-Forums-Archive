---
title: "How do I remove Ubuntu?"
date: 2011-06-24
forum: General Help
---

### Post by hugom on 2011-06-24
No, I'm not giving up on Ubuntu.

I just bought a new computer, and now have Ubuntu on both machines. I would like to remove Ubuntu from my old laptop and install debian on it. But I also want to keep Windows 7 exactly how it is.

The question is how do I remove/uninstall debian? I have googled and most things say that still need my disk for for Windows 7? But I don't have that( I dont't think I ever got it). All I have is a laptop with windows 7 on it and ubuntu.

So, is there a way to remove ubuntu from my computer without making any dramatic changes to windows 7?

Thanks.

---

### Post by garvinrick4 on 2011-06-24
#If you install another Operating System in the partition that Ubuntu is in and you install its boot manager in sda, sdb, sdc whichever drive you are using can boot both Windows and linux.
#If you are using Ubuntu's grub2 as a boot manager and you delete that install, you have
no grub in the mbr (master boot record) to boot off of anymore and without a Windows 7
cd to install a new one to boot windows. Will have to use "Lilo" as a boot manager. (can google Lilo)
#You can get free Windows 7 recovery disks on-line google it download it and burn a CD for yourself.
[Grub/XP/Vista Bootloader - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1014708") 
# I am sure Debian uses grub2 (grub-pc) but I believe you also have to install "os-prober"
as a package seperatly to add other OS's as grub menuentry.

---

### Post by luca5am on 2011-06-24
Did you install ubuntu yourself? Did you install it from windows (Wubi)? Or from the live CD/USB stick?

If you installed it with Wubi, you can uninstall it safely from windows, instructions are here [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide) or there [https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi).

If you installed it yourself from a live CD/USB stick, I guess it is installed on a different  partition from windows (is it even possible to install it on the same  partition as windows in that case?). If it's on a different partition  (which it should be), it is pretty easy to format the corresponding  partition and install a new OS on it by inserting a live CD, which will  not mess up the partition where windows is installed. When you install  ubuntu, there is during config a disk manager that lets you choose what  partition to format and/or use for the installation of the OS. It's the  same for other OSs I guess. Just make sure you know what is installed on  which partition first.

If you didn't install ubuntu yourself, use a partition manager (eg gparted) to see what the situation is.

If you uninstall ubuntu and re-install something else, you might have to  re-install or re-configure the boot manager (grub), although I'm not  sure. There are plenty of guides for that.

Also, make backups before attempting anything.

---

### Post by sidzen on 2011-06-24
I think I'd try using gparted from [SystemRescueCD]("http://sourceforge.net/projects/systemrescuecd/files/sysresccd-x86/1.3.5/") to reformat the same partitions used by the current ubuntu (leaving them blank but reformatted), then download [EasyBCD]("http://neosmart.net/dl.php?id=1") to a USB stick;

To be safe, I'd use Windows to make a rescue/recovery CD for itself *first*, then do a manual install of Debian (using the same reformatted partitions), then install easyBCD, allowing Windows to do its thing at boot.

---

### Post by hugom on 2011-06-24
> **luca5am said:**
> Did you install ubuntu yourself? Did you install it from windows (Wubi)? Or from the live CD/USB stick?

If you installed it with Wubi, you can uninstall it safely from windows, instructions are here [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide) or there [https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi).

If you installed it yourself from a live CD/USB stick, I guess it is installed on a different  partition from windows (is it even possible to install it on the same  partition as windows in that case?). If it's on a different partition  (which it should be), it is pretty easy to format the corresponding  partition and install a new OS on it by inserting a live CD, which will  not mess up the partition where windows is installed. When you install  ubuntu, there is during config a disk manager that lets you choose what  partition to format and/or use for the installation of the OS. It's the  same for other OSs I guess. Just make sure you know what is installed on  which partition first.

If you didn't install ubuntu yourself, use a partition manager (eg gparted) to see what the situation is.

If you uninstall ubuntu and re-install something else, you might have to  re-install or re-configure the boot manager (grub), although I'm not  sure. There are plenty of guides for that.

Also, make backups before attempting anything.

Yeah I did install ubuntu myself on a seperate partition. Could you please elaborate more on how to remove it? I'm quite new to all this. I already have debian downloaded onto a CD but it's not a live CD. Any help on what to do would be great thanks.

---

### Post by mike555 on 2011-06-24
If you installed Ubuntu to a separate partition just install the next operating system on to the same partition and format it during install.formating will erase everything (Ubuntu)on that partition.

---

### Post by luca5am on 2011-06-24
> Yeah I did install ubuntu myself on a seperate partition. Could you  please elaborate more on how to remove it? I'm quite new to all this. I  already have debian downloaded onto a CD but it's not a live CD. Any  help on what to do would be great thanks. 	

First of all back up all important data on an external hard drive or on DVDs.

You can format the ubuntu partition from windows. Or (from the debian installation guide):

"If your machine already has multiple partitions, and enough space can be provided by deleting and replacing one or more of them, then you too can wait and use the Debian installer's partitioning program. You should still read through the material below, because there may be special circumstances like the order of the existing partitions within the partition map, that force you to partition before installing anyway."
From: [http://www.debian.org/releases/stable/i386/ch03s05.html.en](http://www.debian.org/releases/stable/i386/ch03s05.html.en)

In a nutshell, the easiest way to do this is to put a live debian  installation cd, and during the installation, a partition manager will  pop up and you will be able to format the partition you want to use and  select it to install debian. It should be pretty straight forward once  the partition manager pops up.

(debian installation guide: [http://www.debian.org]("http://www.debian.org/"))

---

### Post by jerome1232 on 2011-06-24
> **luca5am said:**
> 

In a nutshell, the easiest way to do this is to put a live debian  installation cd, and during the installation, a partition manager will  pop up and you will be able to format the partition you want to use and  select it to install debian. It should be pretty straight forward once  the partition manager pops up.

(debian installation guide: [http://www.debian.org]("http://www.debian.org/"))

+1 I would just install debian over Ubuntu's old partitions ensuring they get formated. Debian will then add it's bootmanager etc...

---

### Post by hugom on 2011-06-24
> **luca5am said:**
> First of all back up all important data on an external hard drive or on DVDs.

You can format the ubuntu partition from windows. Or (from the debian installation guide):

"If your machine already has multiple partitions, and enough space can be provided by deleting and replacing one or more of them, then you too can wait and use the Debian installer's partitioning program. You should still read through the material below, because there may be special circumstances like the order of the existing partitions within the partition map, that force you to partition before installing anyway."
From: [http://www.debian.org/releases/stable/i386/ch03s05.html.en](http://www.debian.org/releases/stable/i386/ch03s05.html.en)

In a nutshell, the easiest way to do this is to put a live debian  installation cd, and during the installation, a partition manager will  pop up and you will be able to format the partition you want to use and  select it to install debian. It should be pretty straight forward once  the partition manager pops up.

(debian installation guide: [http://www.debian.org]("http://www.debian.org/"))

Ah, thank you. So I will have to have a LiveCD and can't do it from a full installation CD.

Because I noticed the LiveCD size is much smaller than the one I have already burnt and wonder if you miss out on any packages etc.

---

### Post by luca5am on 2011-06-27
I don't think anything is missing on the live CD. The package manager will allow you to easily install anything that would eventually be missing anyway.

---


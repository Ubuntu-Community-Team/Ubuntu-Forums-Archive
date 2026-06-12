---
title: "Grub loading problems"
date: 2010-01-01
forum: General Help
---

### Post by h_ryan503 on 2010-01-01
I have three HDD, one is blank, one has windows, and my main disk is Ubuntu 9.1. I reformatted my blank disk and somehow I couldn't load windows from my grub anymore. I updated grub and windows still wouldn't boot. I fixed the MBR with my windows CD. After that I no longer can get my Grub to come up at all. 

I even took out my Windows drive and my system simply wont boot. I reinstalled Grub from the live CD when my Ubuntu drive was the only one in and it says it works but I still can't boot. I am however able to load my grub if I put in the Live CD and tell it to boot on the first HD. I know I must be missing something simple.

I have followed all the instruction from the links below and no luck. Thanks for any help!

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202")

---

### Post by Herman on 2010-01-01
Your computer looks in what it thinks is the first hard drive for a boot loader in the MBR.

Sometimes, the hard drive your computer's BIOS thinks is the first one is not the same one as Ubuntu thinks is the first drive, or /dev/sda.
This often happens when we have one or two IDE drives and one or two SATA drives plugged in to the same motherboard.
I know, my computer is like that too.

The easiest thing to do is just install GRUB to all your hard drives.

---

### Post by h_ryan503 on 2010-01-01
Thank you!!!

My problem was two fold.

The moment I put Grub on my other drives it loaded. I'm not sure why my system didn't load the drives in the order I put on my BIOS but it doesn't matter for this thread.

Second, when I installed Grub on the NTFS windows drive I put the command in wrong and it was looking for grub.cfg on that drive. So if someone reads this in the future make sure you run:
```
sudo grub-install --root-directory=/WindowsDrive /dev/sdX
```

Were sdX is the Linux drive :)

---

### Post by Leppie on 2010-01-01
[removed]

---

### Post by Leppie on 2010-01-01
> **h_ryan503 said:**
> The moment I put Grub on my other drives it loaded. I'm not sure why my system didn't load the drives in the order I put on my BIOS but it doesn't matter for this thread.
why do you set a drive order in your bios to then change it in grub?

> **h_ryan503 said:**
> Second, when I installed Grub on the NTFS windows drive I put the command in wrong and it was looking for grub.cfg on that drive. So if someone reads this in the future make sure you run:
```
sudo grub-install --root-directory=/WindowsDrive /dev/sdX
```

Were sdX is the Linux drive :)

the command you issued here actually installs grub2 to the windows drive. i wouldn't advice to do that. i think that especially since you had a dedicated windows drive, you shouldn't have installed grub there. you can chainload your windows boot loader from grub2 in an easy way. now when you remove ubuntu from this system, you will have to restore your windows in a much more complicated way (removing ubuntu will still leave you with grub2 installed on the windows drive and partition).

I would strongly advise other users **_*not to do*_** what you have done.

---

### Post by Herman on 2010-01-01
```
sudo grub-install /dev/sda
```[FONT=monospace]
[/FONT]```
sudo grub-install /dev/sdb
```[FONT=monospace]
[/FONT]```
sudo grub-install /dev/sdc
```
You only want to install the IPL for GRUB to all of your hard disks, not GRUBs files and directories as well.

The MBR is not part of the Windows file system.

---

### Post by Herman on 2010-01-01
> now when you remove ubuntu from this system, you will have to restore your windows in a much more complicated way (removing ubuntu will still leave you with grub2 installed on the windows drive and partition).:) Well, now that it's done it's done. I wouldn't advise anyone to do that either, I should have given the commands earlier.
But since GRUB2 has an ntfs.mod, I'm thinking that possibly this will be okay. 
Removing Ubuntu will not affect anything now if he will have GRUB2 in Windows. It might actually turn our to be a good thing. I would be interested in experimenting with that myself to se what happens. I didn't mean to tell anyone else to do that though.

---

### Post by Leppie on 2010-01-01
usually the issue is solved best by using the uuid's (Universal Unique Identifier).

---

### Post by Herman on 2010-01-01
First the BIOS looks in the MBR of the first hard disk to find the IPL to point to a boot loader either in the first track of the hard disk or in a file system, or it relays the boot via a boot sector.

The BIOS will only look in the first hard disk,
except if the user presses F8 for a boot menu and deliberately tells the BIOS to boot a different disk by the MBR.

After that, when the actual boot loader program is engaged, the boot loader should try to boot the operating system requested by the user.
From there, UUID numbers are useful for specfying exactly which file system to use, no matter what hard disk and partition the operating system will be in.

But first we had to help the BIOS find the boot loader.

h_ryan503's problem was his BIOS wasn't finding a MBR which contained code to point to GRUB.
Most likely the GRUB IPL code was in a different MBR.
By installing a little code in all the hard disk's MBRs, h_ryan503's PCs BIOS will be redirected to GRUB no matter which hard disk it looks in.

The MBR of any hard disk is in sector zero, the first sector, of each hard disk.
No operating system partition begins until at least after the first track of a hard disk, sector 63.
To prove it, you can check with the fdisk -lu command.
```
sudo fdisk -lu
```So by installing GRUB to any hard disk's MBR you are not writing to any other operating system.
It's safe to install the IPL (code pointing to GRUB), in all hard disk MBRs, even if a hard disk contains Windows.

It was an accident and my mistake that I didn't specify the exact commands for h_ryan503 in the first place. That command, if the NTFS partitions was mounted, would have created a /boot/grub directory in h_ryan503**'**s Windows and filled it with GRUB files. 
Not so long ago when Linux didn't have such good NTFS support, that probably would have been dangerous for the Windows installation.
I'm not sure about that now, it wouldn't be particularly recommendable, but I'm curious and I'm going to run a few tests here myself and see what happens. :)

---

### Post by Leppie on 2010-01-01
> **Herman said:**
> I'm not sure about that now, it wouldn't be particularly recommendable, but I'm curious and I'm going to run a few tests here myself and see what happens. :)
it doesn't really break anything (the ntfs-3g module now has excellent ntfs support). it's just that if he decides to use the windows disk on it's on in this system, it will still come up with the grub2 menu as it's installed on that disk.

---

### Post by Herman on 2010-01-01
> it doesn't really break anything (the ntfs-3g module now has excellent ntfs support).:) Cool! I'm getting ready to try it out!
> it's just that if he decides to use the windows disk on it's on in this system, it will still come up with the grub2 menu as it's installed on that disk.:) That's what I expect too. Actually, that will make his computer more reliable in one way, because if he ever uninstalls Ubuntu his Windows will still keep booting as normal. It will be the same as having a 'Dedicated GRUB Partition', except it's inside his Windows partition instead of in a separate partition of its own.
In another way of thinking it will be slightly less convenient when he needs to re-install Windows. It will just mean he'll need to either boot a different MBR or re-install GRUB again.
Also, the Ubuntu installation won't be keeping his grub.cfg updated automatically. 
It would be simple enough to use the grub-mkconfig command with a file path to the Windows GRUB to update it though. :)

---

### Post by Leppie on 2010-01-01
> **Herman said:**
> Actually, that will make his computer more reliable in one way, because if he ever uninstalls Ubuntu his Windows will still keep booting as normal. It will be the same as having a 'Dedicated GRUB Partition', except it's inside his Windows partition instead of in a separate partition of its own.
with grub not modifying the windows drive at all (neither mbr nor windows partition), windows obviously will boot normally. having grub on a pure windows system doesn't really seem to add any advantages. furthermore i'm not sure if grub would be able to retrieve the configuration file from the windows partition as the harddrives setup will have changed.

---

### Post by Herman on 2010-01-01
> with grub not modifying the windows drive at all (neither mbr nor windows partition), windows obviously will boot normally.If I'm understanding the situation correctly, h_ryan503 installed GRUB2 inside the Windows file system, and the IPL pointing to it to MBR in the same hard disk. But I'm not certian about that, because the command he has offered actually says '/dev/sdx' as the MBR. 
I'm *presuming* he installed GRUB to all MBRs.
If that's so then his Windows will boot via the new copy of GRUB in the Windows partition, which will chainload the Windows boot sector and thus engage the Windows boot loader, which will then boot Windows. It will be a more lengthy sequence of operations, it might slow down booting Windows slightly, but that would be negligable.
>  having grub on a pure windows system doesn't really seem to add any advantages. Only if something happens to Ubuntu, Windows will remain bootable.
> furthermore i'm not sure if grub would be able to retrieve the configuration file from the windows partition as the harddrives setup will have changed.:) He can use the grub-mkconfig command like this,
```
sudo grub-mkconfig -o /media/WindowsDrive/boot/grub/grub.cfg
```, Where: the Windows file system is mounted as /media/WindowsDrive, 
and where: his GRUB directory is /boot/grub.

Ubuntu won't update his grub.cfg automatically with a kernel update, but if he runs that command himself it will.

However, it's not something I'd particularly advise anyone to do on purpose.
It might be an idea to treat it like a Dedicated GRUB Partition and  modify the grub.cfg to chainload GRUB in Ubuntu so the Ubuntu's grub.cfg will be used for booting Ubuntu. That one will be automatically kept up to date.

---


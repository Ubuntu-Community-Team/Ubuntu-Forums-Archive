---
title: "Clonezilla Restore: Where does Grub reside?"
date: 2011-09-13
forum: General Help
---

### Post by amhainen on 2011-09-13
My hard drive started clicking and wouldn't boot this weekend. LUCKILY, I made a Clonezilla image just 2 days before. Let me give a little premise and what I did to fix this (maybe I can help others) and then I have a few questions so I can learn what I did and how Grub works:

I have three operating systems on my computer:

sda1=reserve
sda2=**Win7ProX64**
sda4=extended
sda5=**Ubuntu 10.04 X64**
sda6=swap
sda7=**Ubuntu 11.04**

Prior to the failure, I was running just Win7/10.04 for a long time. Later, I decided to install 11.04. After the install of 11.04, I noticed that Grub changed from a black background to a purple background. My guess is that when I installed 11.04, it put on a newer version of Grub. It was okay as everything worked fine. I could run the GUI Start-Up Manager in 11.04 and everything worked fine.

After I restored the Clonezilla image to my new hard drive this evening, Grub defaulted right into Win7 like I had it set, but I noticed a black background in Grub (indicating perhaps it reverted to the 10.04 Grub?). Everything was fine in Windows land, so I rebooted and was going to fix the three files listed on the [UsingUUID Ubuntu]("https://help.ubuntu.com/community/UsingUUID") documentation starting with my 10.04 partition:

[LIST]
[*]/boot/grub/menu.lst
[*]/etc/fstab
[*]/etc/initramfs-tools/conf.d/resume
[/LIST]

I ran "sudo blkid" and everything matched up. I rebooted and I went to boot my 11.04 and Grub couldn't find the kernel. I rebooted to my 10.04, chrooted to the 11.04 partition and found the kernel version was newer than the command in Grub. I rebooted and hit "e" in Grub and update the kernel number. Also, I had to change the file system from ext2 to ext4 (I'm not sure how this changed). Almost done: I got into 11.04 and ran the [GUI Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair"). I rebooted and found that Grub had a purple screen and I could boot into 11.04 just fine!

Okay, now I have some questions:

[LIST=1]
[*]Where does Grub reside? I think I was sort of lucky figuring out which OS was managing Grub based on the background color. Does Grub get installed on the same partition of the OS that it's administered through? Or is there another partition or sector where it's installed?

[*]What is the non-GUI way to fix this? I tried "sudo update-grub2" in 11.04, but when I rebooted it just went back to the black Grub which I think was the 10.04 Grub.

[*]How did the new UUID as identified in "sudo blkid" get updated after I reimaged my new hard drive? I read that this had to be done manually, but everything looked good to me.

[*]Sort of a strange question, but was this an okay way to fix it? I don't know much about computers, but I want to make sure I'm doing things right.
[/LIST]



Thanks for all the help with the questions above. Hopefully someone else finds this useful.

---

### Post by Quackers on 2011-09-13
Grub (or the first bit of it) is stored in the first sector of the hard drive - known as the MBR of the drive. This is before any partition.
I have had problems with Clonezilla. Sometimes that first sector is backed up but does not restore. Other times it works fine. I don't know why that happens, so can't comment further.
It looks like your restore somehow put 10.04's version of grub in control.
/boot/grub/menu.lst is not used by grub2. That file was used by grub legacy only.

There are different methods of fixing grub problems, but often it would involve chrooting from a live cd and re-installing grub.

The UUID's should be the same as they were when the partitions were copied.
Updating UUID's would only need doing when a cloned system is put on a different machine, I suspect.

When there is a problem you fix it any way you can :-)

---

### Post by amhainen on 2011-09-13
> **Quackers said:**
> Grub (or the first bit of it) is stored in the first sector of the hard drive - known as the MBR of the drive. This is before any partition.

 
Thanks for your reply! How does Grub know which partition to look at for its config file? I would guess it's defined when Grub is installed, but is there any way that I can pick which partition or OS controls Grub? Also, does the bootable flag in fdisk relate to this?
 
Thanks again!

---

### Post by Quackers on 2011-09-13
Boot flags are not used by Linux systems, only Windows uses them.

If you take the case where grub needs to be re-installed for some reason.
You first mount the root partition of the affected system to /mnt, for instance.
Once that is mounted you can install the first bit of grub to the MBR of the drive. Because the root partition was mounted first grub knows where to find its boot files (which are in that root partition).

If you have multiple Ubuntu systems on the same machine you can boot the system that you want to have control of grub and run ```
sudo grub-install /dev/sda
``` (change the drive designation as necessary) which will install grub to the MBR of the drive.

Obviously there is only one MBR of a hard drive, so the most recently installed grub has control.

---


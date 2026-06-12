---
title: "How to best format HD-dual boot"
date: 2012-08-06
forum: General Help
---

### Post by tajreed on 2012-08-06
for Win 7 when Ubuntu is already installed. I've tried by freeing up space and formatting to ntfs.  But when Win starts, I get "Win can't find a suitable partition." Where should the Win partition be on the HD? Or does it not matter.

Thanks

---

### Post by GreatDanton on 2012-08-06
It doesn't matter. Delete the partition where you want to have your Windows and don't format it! Leave it like it is and Windows installer will take care then. Also keep in mind you will have to make boot repair afterwards.

Regards.

---

### Post by 3Miro on 2012-08-06
Windows needs a small primary partition to boot. Leave empty space and let Windows 7 format it, although you do need to leave space for a primary partition.

Otherwise, you need to reformat the HDD and probably delete Ubuntu.

---

### Post by tajreed on 2012-08-06
Do I need two partitions, one small for boot and one for all else. And neither are to be formatted? I had one 25g partition formatted and it didn't work. Also tried without formatting. Still didn't work. 'Win can't find appropriate partition....'.

---

### Post by Bucky Ball on 2012-08-06
Windows needs more than one partition nowadays. DON'T create any partitions, delete the NTFS one you created and just leave free space *at the beginning of the disk* so Windows can be first hard drive (sda in Linux, hd0 in Win), first partition. It likes that (anywhere else is a tweaking headache but do-able). Then partition that free space you left as you're installing Win.

So, first drive, first primary partition (MUST be a primary partition). Ubuntu will happily live on a logical partition inside an extended.

Once Win is installed you will lose Ubuntu boot. You will need to re-install grub using a LiveCD. Good luck. ;)

PS: If you have four or more primary partitions on the drive already you are screwed. That is why you are getting the message, regardless of free space or empty partitions. That is the max. BUT, you can have three primaries (two for Win) and an extended, inside which you can theoretically have as many logical partitions as your hardware can handle.

PPS: This is the long version of what 3Miro said ... ;)

PPPS: The 'more than one partition required for Win' is only applicable for newer releases. XP only requires ONE partition.

---

### Post by tajreed on 2012-08-07
Thanks for the tips. I'll give it a try later today.

---

### Post by Mr. Beekeeper on 2012-08-07
I'm kind of limited in my knowledge, so take this with a grain of salt...

I would format this way if possible:

Windows 7: 40 gigs of space, ntfs

Ubuntu: 15 gigs of space, ext4, mount point "/"

Dual access storage space: whatever's left - twice your RAM, ntfs

swap space for Ubuntu: your RAM x 2, linux swap space

This way, you'll be able to store anything in the "Dual Access" area and have it visible on both systems, You'll also be able to re-install either OS without losing any data on the Dual Access area.  It's nice to be able to then try out different versions of Linux without data loss.  I hoped this helped a little, like I said, I'm sure the veterans will correct me on some points, but this type of setup has worked well for me.

---

### Post by Bucky Ball on 2012-08-07
> **Mr. Beekeeper said:**
> I'm kind of limited in my knowledge, so take this with a grain of salt...

No offence, but in that case, why didn't you read the other posts on this thread?

---

### Post by Mr. Beekeeper on 2012-08-07
> **Bucky Ball said:**
> No offence, but in that case, why didn't you read the other posts on this thread?


OK, just trying to help... You're the expert,  I'll keep out of your threads from now on.

---

### Post by tajreed on 2012-08-08
This shouldn't be this difficult. I managed to get a Win partition as second position on hard drive but still won't install, "Win can't find suitable partition...".

First position on drive is SDA 1, boot for Ubuntu.. I can't figure out how to move the SDA1 to the right and have the Win partition be first on the drive. I've been using PartedMagic live. Very good by the way. And at least I'm learning about moving/resizing partitions. 

I'm guessing that the Win partition must be Primary but there seem to be no options to make it so.

Any thoughts?

---

### Post by oldfred on 2012-08-08
You can only have 4 primary partitions, so did you use all 4 already? Windows has to be primary NTFS formated with the boot flag. So it must be sda1 thru sda4. 

While better to be first it does not have to be. But some have reported when installed after the extended partition the partitions get changed. I would also back up partition table just in case to have the details.

Backup partition table to text file & save to external device.
sudo sfdisk -d /dev/sda > PTsda.txt

---

### Post by tajreed on 2012-08-08
Here's what I have.
sda1 boot
sda2 extended
unallocated
sda5 home
sda6 swap

How do I make unallocated into a Primary ntfs? gparted won't allow formatting of Unallocated as primary.

---

### Post by oldfred on 2012-08-08
If the unallocated is in the extended, you have to shrink the extended partition so you can make a primary partition.

It looks like sda1 is really / (root) not boot, but is perhaps labels with the boot flag. You have to move the boot flag to the NTFS partition you create. Right click and set boot flag.

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

---

### Post by tajreed on 2012-08-08
Turns out to be simple, as is usually the case. As instructed, resized the extended partition and was instantly able to create NTFS primary partition. Win 7 installing now.

Thanks to OLDFRED and everyone else for their help.

---

### Post by oldfred on 2012-08-08
It is only easy when you know how. :) Glad you have that solved.

Windows will install its boot loader, so you have to reinstall grub2's boot loader. And then you can update the grub2 menu to add the Windows entry.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 - grub2) - talsemgeest
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)

If you prefer a gui, you can download this into your Ubuntu liveCD or download as a full liveCD.
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration an diagnose advanced problems.

After you boot Ubuntu, then run this to add Windows to grub's menu.

sudo update-grub

Some have reported partition issues after a Windows install. If you have any you may need testdisk but post back and if possible run BootInfo from Boot-Repair.

---

### Post by tajreed on 2012-08-08
Boot-Repair worked using a live Ubuntu. I'm in business. Thanks

---

### Post by Bucky Ball on 2012-08-08
Excellent. Please mark thread as solved to help others. ;)

---

### Post by Austin Texas on 2012-08-08
You do have to move the Ubuntu partition. Windows wants that first partition - sda1. Send Bill Gates a "Thank You" note.
You can move the Ubuntu partition and leave unallocated space at the beginning of the drive. gparted will do that. Just right-click on the partition and you can move it to the right. Of course, you have to have unallocated space to move it into...
grub2 uses UUID, and that won't change, so I don't think the move will cause any problem with booting Ubuntu.

---

### Post by Bucky Ball on 2012-08-08
As Austin T says, BUT, to do this you need the partition to be unmounted. Therefore boot from the LiveCD to do this.

And ... BACKUP. You are moving the entire OS and it will take awhile. The Ubuntu boot and presumably your info are on there and nothing's foolproof. ;)

---


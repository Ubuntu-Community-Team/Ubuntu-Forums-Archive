---
title: "Serious partition problems. Please help"
date: 2010-10-06
forum: General Help
---

### Post by Oskarelli on 2010-10-06
Hi 

Seems that i have totally ****ed up my sony vaio (vgn-fz21z). I've been doing some partitioning and formatting without really knowing what i was doing. Now it is a mess.

The vaio comes with pre-installed windows vista, which is no longer installed. I want it to be. Ubuntu 10.4 is installed. 

In grub I can  choose vista but that is only vaio recovery tool. Which is not working. When I try the format c:-option and take it all back to the original settings, it says that c: is too small or missing. 

I also have some cd:s with windows 7 and xp on, but they can't be read. Now the vaio is not even accepting my ubuntu live-cd. 

I have nothing of importance on the computer, so there would be no problem re-formatting the whole thing. Can it be done? I would prefer is the vaio recovery tool could be left untouched, it has its own partition. 

I guess I'm asking: is there a way from inside ubuntu to make a total system re-installation, get rid of different partitions and reconstruct c:, so win can be installed again?

Hope anyone can help me! /oskar

---

### Post by corruptor1972 on 2010-10-06
Hi,

Sorry to hear about your computer  :(

I'm not sure what you mean by the computer not accepting the CD.  Is the CD drive plugged in correctly and the BIOS on the machine set to boot from the CD drive first?

If you still can't get the CD drive to work, there's always the USB option.  I suggest that you [_create an Ubuntu Live System on a USB stick_]("https://help.ubuntu.com/community/Installation/FromUSBStick") and boot Ubuntu from that.

I restored a Dell machine recently after its Hard Drive was trashed by a drop.  After the new Hard Drive was installed, I had to create partitions in the same layout and of roughly the same sizes as they were on the original HD:  For this I used Ubuntu's excellent Gparted program.  I then used [_FreeDos_]("http://www.freedos.org/") (which I believe can also be run from a USB stick) to kick off the restore process.  I had to guess what .bat or .exe file to run to start the restore, but it did work.

I don't have a Vaio so I can only give you general suggestions, but I hope this helps you.

---

### Post by Oskarelli on 2010-10-06
> **corruptor1972 said:**
> Hi,

Sorry to hear about your computer  :(

I'm not sure what you mean by the computer not accepting the CD.  Is the CD drive plugged in correctly and the BIOS on the machine set to boot from the CD drive first?

If you still can't get the CD drive to work, there's always the USB option.  I suggest that you [_create an Ubuntu Live System on a USB stick_]("https://help.ubuntu.com/community/Installation/FromUSBStick") and boot Ubuntu from that.

I restored a Dell machine recently after its Hard Drive was trashed by a drop.  After the new Hard Drive was installed, I had to create partitions in the same layout and of roughly the same sizes as they were on the original HD:  For this I used Ubuntu's excellent Gparted program.  I then used [_FreeDos_]("http://www.freedos.org/") (which I believe can also be run from a USB stick) to kick off the restore process.  I had to guess what .bat or .exe file to run to start the restore, but it did work.

I don't have a Vaio so I can only give you general suggestions, but I hope this helps you.
Hi 

Thanks for quick reply.

The cd drive (and ubuntu-cd) was working just fine earlier today but not anymore. But I have ubuntu installed and can boot it from grub. I have also Gparted, that is what has mixed things up for me.

I will look into freedos. Do you think i can use that to make everything be c: (+ vaio recovery) again?

/oskar

---

### Post by coffeecat on 2010-10-06
When you first got the Sony, did you make a set of restore DVDs when it prompted you repeatedly to do so? If not, then the recovery partition may be able to restore Vista for you. So don't do anything which might delete the recovery partition (which is sda1). If you do, you will lose Vista for ever if you don't have the set of recovery DVDs.

> **Oskarelli said:**
> In grub I can  choose vista but that is only vaio recovery tool. Which is not working. When I try the format c:-option and take it all back to the original settings, it says that c: is too small or missing. 

Sounds as though it is working just fine. The "C: is too small" message is telling you something, no? The recovery partition can restore Vista plus all the bundled apps back to factory condition, but only if there is a large enough C: (sda2) NTFS partition. It sounds as though you deleted it or made it too small when you installed Ubuntu. You need to make sda2 larger - at least 40GB I would think, or nearer 80-100 - so that the recovery partition can do its work. **Edit:** which will be difficult seeing that you can't boot from a CD.

On my Sony Vaio, I can boot into the recovery partition by pressing an F-key before the grub menu comes up. Do you have that?

---

### Post by Quackers on 2010-10-06
I think mine is F11 during boot to enter the Recovery Environment.
FYI take care with sda1 and sda2. Grub can label them the wrong way round - so that sda1 is actually your live Windows system and sda2 can be your Recovery partition!

---

### Post by coffeecat on 2010-10-06
> **Quackers said:**
> FYI take care with sda1 and sda2. Grub can label them the wrong way round - so that sda1 is actually your live Windows system and sda2 can be your Recovery partition!

Good point! I believe Sony *usually* puts the recovery partition on sda1 and C: on sda2 with XP or Vista systems, but I'm prepared to be corrected. (Windows 7 complicates things with the small boot partition.)

On my Vaio with Vista, Maverick's grub2 has listed my sda1 recovery partition as "Windows Vista (loader)" and the sda2 C: partition as "Windows Recovery Environment". :|

---

### Post by Quackers on 2010-10-06
You're absolutely correct coffeecat, on my installation Grub labels them wrongly. It did it with Lucid too. It's not a Sony thing, just a Grub thing.

---

### Post by coffeecat on 2010-10-06
> **Quackers said:**
> It's not a Sony thing, just a Grub thing.

Agreed entirely, but it gets worse...

> **coffeecat said:**
> On my Vaio with Vista, Maverick's grub2 has listed my sda1 recovery partition as "Windows Vista (loader)" and the sda2 C: partition as "Windows Recovery Environment". :|

But both entries boot me into Vista's C: on sda2, even though the stanzas in grub.cfg look OK to me - except for giving sda1 and sda2 the wrong names. 

I shall investigate further. :-k

---

### Post by Quackers on 2010-10-06
Ah. On mine if I choose the entry with Vista Loader (sda2) it boots the Recovery partition and vice versa.

---

### Post by Oskarelli on 2010-10-08
> **coffeecat said:**
> When you first got the Sony, did you make a set of restore DVDs when it prompted you repeatedly to do so? If not, then the recovery partition may be able to restore Vista for you. So don't do anything which might delete the recovery partition (which is sda1). If you do, you will lose Vista for ever if you don't have the set of recovery DVDs.



Sounds as though it is working just fine. The "C: is too small" message is telling you something, no? The recovery partition can restore Vista plus all the bundled apps back to factory condition, but only if there is a large enough C: (sda2) NTFS partition. It sounds as though you deleted it or made it too small when you installed Ubuntu. You need to make sda2 larger - at least 40GB I would think, or nearer 80-100 - so that the recovery partition can do its work. **Edit:** which will be difficult seeing that you can't boot from a CD.

On my Sony Vaio, I can boot into the recovery partition by pressing an F-key before the grub menu comes up. Do you have that?

Hi there

Thanks for the replies. I've been away for a couple of days, that is why no answer.

I didn't make any recovery dvd:s when I bought the vaio. But I haven't touched the recovery partition so it is still working. It boots when I choose Vista (loader) in Grub.

Yes, I guessed that sda2 should be made larger. But it is large enough, and is still not working. Here is what sudo fdisk -l shows:

Device       Boot            Start              End         Blocks            Id       System
/dev/sda1      *                      1                1627         13063168        27     Unknown
/dev/sda2                 1628    18897       138719347+    7       HPFS/NTFS
/dev/sda3                          18897   36482         141247489       5        Extended
/dev/sda5                          18897         35762         135469056      83      Linux
/dev/sda6                          35763         36482       5777408          82      Linux swap / Solaris

From what I can tell, the sda1 is the recovery partition, sda3,5,6 is Ubuntu and sda2 is what should be c: (windows). As you ca see, it is 138 GB. I don't know what HPFS is. And vaio recovery tool still says c: is too small or not existing.

Is there a way to reformat sda2 to a clean NTFS? Will that work or do I have to label it c: somewhere? Should the partition be mounted or unmounted? Any other clues?

Thanks /oskar

---

### Post by coffeecat on 2010-10-08
I presume that fdisk output is from your hard drive Ubuntu install since you say the optical drive is not working.

> **Oskarelli said:**
> I don't know what HPFS is.

[HPFS.]("http://en.wikipedia.org/wiki/High_Performance_File_System") HPFS and NTFS use the same filesystem ID number in the partition table. Your C: partition wlll be NTFS; you can ignore the HPFS bit.

> **Oskarelli said:**
> sda2 is what should be c: (windows). As you ca see, it is 138 GB.

Actually, I can't since you didn't post the first bit of the output of fsdisk, which gives the unit size. Assuming that is 8225280 bytes, then I calculate sda2 to be 132.3 GiB. But plenty big enough.

> **Oskarelli said:**
>  Is there a way to reformat sda2 to a clean NTFS?

That's probably what I would do next. Perhaps the C: filesystem is corrupted and the recovery utility interprets that as too small or missing. You can use Gparted in Ubuntu. You may need to install ntfsprogs first though. It comes in a default install in Maverick but in earlier versions you had to install it if you were using Gparted in your hard drive install. I can't remember whether it comes with 10.04 or not, so check that first. Simply open Gparted, highlight sda2, Partition menu > Format to > ntfs. That will give you a clean NTFS filesystem for the recovery utility to work from.

But, I noticed one thing...

> **Oskarelli said:**
> Here is what sudo fdisk -l shows:

Device       Boot            Start              End         Blocks            Id       System
/dev/sda1      *                      1                1627         13063168        27     Unknown
/dev/sda2                 1628    18897       138719347+    7       HPFS/NTFS

The boot flag is set on sda1, not on sda2. Is the problem with your Windows C: is that it will not boot? Normally, Windows needs the boot flag set and you can only have a boot flag set on one partition at a time. As far as I remember, Windows can boot without the boot flag if done from grub, but I might be wrong. If your original problem was a simple failure of Vista booting, you could try setting the boot flag in sda2. You can do this easily from Gparted (Partition > Manage Flags).

---

### Post by srs5694 on 2010-10-08
> **Oskarelli said:**
> I didn't make any recovery dvd:s when I bought the vaio. But I haven't touched the recovery partition so it is still working. It boots when I choose Vista (loader) in Grub.

Normally, type-0x27 partitions, such as your /dev/sda1, serve as emergency repair systems; they  can be used to check the disk and fix other common boot-time problems,  but they can't completely re-install Windows to a partition that's  damaged beyond repair. That task is relegated to a separate system recovery partition or to a system installation DVD. OTOH, your /dev/sda1 is unusually large (13GB, if I'm counting the digits correctly). That's large enough to hold the files necessary for a complete installation. Thus, it's conceivable you've got everything you need to re-install Windows. I can't be positive of that, though.

If /dev/sda1 cannot re-install Windows, then if you computer came with a Windows restore/recovery DVD, you may have to use it. If the computer didn't come with such a disc, you may have to contact Sony to get a full system restore DVD. (No doubt they'll charge you for it.) Alternatively, you could buy a retail version of Windows 7; however, if you get an upgrade version, it might not install, given the damage to your Vista installation.

> I don't know what HPFS is.

It's a filesystem used by very early versions of Windows NT and OS/2. It uses the same partition type code as NTFS, so fdisk can't tell HPFS and NTFS partitions apart.

> Is there a way to reformat sda2 to a clean NTFS? Will that work or do I have to label it c: somewhere? Should the partition be mounted or unmounted? Any other clues?

You can certainly use GParted or the text-mode mkfs or mkfs.ntfs to re-initialize /dev/sda2 to NTFS; however, doing so will require you to completely re-install Windows. Your /dev/sda1 recovery partition may not be sufficient to do this, since it might not include a full copy of the installation disc set, as noted above. Linux doesn't use drive letters ([noparse]C:, D:,[/noparse] etc.), and they aren't encoded in the filesystem, so if you use Linux to initialize a partition as NTFS, you can't give it a drive letter in Linux; Windows will assign one automatically when it uses the partition. Whenever you create a filesystem on a partition, that partition *must* be unmounted. For your purposes, whether you mount it after that is irrelevant, since Linux won't be running when you re-install Windows.

One other comment: You might want to use ntfsclone to back up your current /dev/sda2 before you do anything else, assuming you've got the space to do it and assuming that the utility will work on your damaged filesystem. If you back up, you'll be able to restore it if you run into problems and want to revert to try another approach.

---

### Post by Oskarelli on 2010-10-11
> **srs5694 said:**
> Normally, type-0x27 partitions, such as your /dev/sda1, serve as emergency repair systems; they  can be used to check the disk and fix other common boot-time problems,  but they can't completely re-install Windows to a partition that's  damaged beyond repair. That task is relegated to a separate system recovery partition or to a system installation DVD. OTOH, your /dev/sda1 is unusually large (13GB, if I'm counting the digits correctly). That's large enough to hold the files necessary for a complete installation. Thus, it's conceivable you've got everything you need to re-install Windows. I can't be positive of that, though.

If /dev/sda1 cannot re-install Windows, then if you computer came with a Windows restore/recovery DVD, you may have to use it. If the computer didn't come with such a disc, you may have to contact Sony to get a full system restore DVD. (No doubt they'll charge you for it.) Alternatively, you could buy a retail version of Windows 7; however, if you get an upgrade version, it might not install, given the damage to your Vista installation.



It's a filesystem used by very early versions of Windows NT and OS/2. It uses the same partition type code as NTFS, so fdisk can't tell HPFS and NTFS partitions apart.



You can certainly use GParted or the text-mode mkfs or mkfs.ntfs to re-initialize /dev/sda2 to NTFS; however, doing so will require you to completely re-install Windows. Your /dev/sda1 recovery partition may not be sufficient to do this, since it might not include a full copy of the installation disc set, as noted above. Linux doesn't use drive letters ([noparse]C:, D:,[/noparse] etc.), and they aren't encoded in the filesystem, so if you use Linux to initialize a partition as NTFS, you can't give it a drive letter in Linux; Windows will assign one automatically when it uses the partition. Whenever you create a filesystem on a partition, that partition *must* be unmounted. For your purposes, whether you mount it after that is irrelevant, since Linux won't be running when you re-install Windows.

One other comment: You might want to use ntfsclone to back up your current /dev/sda2 before you do anything else, assuming you've got the space to do it and assuming that the utility will work on your damaged filesystem. If you back up, you'll be able to restore it if you run into problems and want to revert to try another approach.

Hi guys

I've now re-formatted the sda2 to NTFS in Gparted. First it didn't work, but when I changed "boot"-flag to sda2, the recovery tool no longer said "too small or missing". Instead, it started to re-format, and I was happy. 

Unfortunately, it lasted for less than one second. The it stopped, and said the following: "Could not obtain the target drive letter". When I chose "Ok" (the only choise available), it said "Task failed with error: -1".

Any ideas? You said that linux dosen't use drive letters, but it seems the recovery tool want one. Is there any way I can fix this?

Thanks /oskar

---

### Post by coffeecat on 2010-10-11
> **Oskarelli said:**
> Hi guys

I've now re-formatted the sda2 to NTFS in Gparted. First it didn't work, but when I changed "boot"-flag to sda2, the recovery tool no longer said "too small or missing". Instead, it started to re-format, and I was happy. 

Unfortunately, it lasted for less than one second. The it stopped, and said the following: "Could not obtain the target drive letter". When I chose "Ok" (the only choise available), it said "Task failed with error: -1".

Any ideas? You said that linux dosen't use drive letters, but it seems the recovery tool want one. Is there any way I can fix this?

By recovery tool, I presume you mean the Sony recovery partition. This is Windows based - this is why it is referring to drive letters. Linux has nothing to do it. The fact that you used a Linux app to reformat the partition is immaterial. Anyway, from what you say, it reformatted the already-reformatted NTFS partition. Thereafter, the problem seems to be with the recovery utility.

Since I last posted in this thread, I found that my Sony recovery utility had autocorrupted itself somehow, which is why I could neither boot into it nor start it with F10. I have since done a complete system restore with the DVDs I made and I now have a working recovery partition.

It could be that your recovery partition is also damaged. Or it might be worth googling that error message. If that doesn't turn up anything useful then all I can suggest is:

1 Try a complete system restore, rather than just a C: drive restore with the recovery utility. That will wipe out your Linux partitions, so back up everything you need first and be prepared to reinstall Ubuntu. If you manage this successfully, before you do anything else, boot into Vista and **make a set of recovery DVDs**. No, make that two sets. :wink:

2 If that doesn't work then your recovery partition is truly broken. Then, if you want Vista back, your only option would be to contact Sony and see how much a set of restore DVDs would cost. They will supply them; I guess they would not be cheap.

---

### Post by Oskarelli on 2010-10-11
> **coffeecat said:**
> 

It could be that your recovery partition is also damaged. Or it might be worth googling that error message. If that doesn't turn up anything useful then all I can suggest is:

1 Try a complete system restore, rather than just a C: drive restore with the recovery utility. That will wipe out your Linux partitions, so back up everything you need first and be prepared to reinstall Ubuntu. If you manage this successfully, before you do anything else, boot into Vista and **make a set of recovery DVDs**. No, make that two sets. :wink:

2 If that doesn't work then your recovery partition is truly broken. Then, if you want Vista back, your only option would be to contact Sony and see how much a set of restore DVDs would cost. They will supply them; I guess they would not be cheap.

Thanks for reply.

1. Problem is, I don't have the option "complete system restore" in vaio recovery utility. I just have c: drive restore.
2. When I called sony and asked for a recovery cd, they said that the cd contains exactly the same as the recovery utility installed on my vaio. 

I have no files or nothing on the computer that is important, so it would be ok for me to erase everything and start up blank. If I just knew how to do it. The only thing I'm worried about is that if I do it, nothing will work because the dvd-drive is not working.

Thanks /oskar

---

### Post by coffeecat on 2010-10-11
> **Oskarelli said:**
> 1. Problem is, I don't have the option "complete system restore" in vaio recovery utility. I just have c: drive restore.

That's very curious. I've had two (different) Sony Vaio laptops in the last five years and the recovery options were very comprehensive. They even allowed you flexibility in the size of the Windows "C:" partition to be restored. 

> **Oskarelli said:**
> 2. When I called sony and asked for a recovery cd, they said that the cd contains exactly the same as the recovery utility installed on my vaio.  Well - I would hope that the Sony people know what they are talking about. By the way, it wouldn't be just one CD. My Vista Sony made three restore DVDs and my older XP Sony two DVDs - or a huge pile of CDs.

> **Oskarelli said:**
> I have no files or nothing on the computer that is important, so it would be ok for me to erase everything and start up blank. If I just knew how to do it. The only thing I'm worried about is that if I do it, nothing will work because the dvd-drive is not working.

I'd forgotten about the non-functional DVD drive - sorry. That does rather limit your options and would have made recovery DVDs superfluous. I don't know what else to suggest.

Perhaps Quackers can think of something.

---

### Post by Oskarelli on 2010-10-11
Alright, thanks anyway. I'll let you know if there is ever a solution.

cheers /oskar

---

### Post by corruptor1972 on 2010-10-16
> **Oskarelli said:**
> Hi 

Thanks for quick reply.

The cd drive (and ubuntu-cd) was working just fine earlier today but not anymore. But I have ubuntu installed and can boot it from grub. I have also Gparted, that is what has mixed things up for me.

I will look into freedos. Do you think i can use that to make everything be c: (+ vaio recovery) again?

/oskar

Out of curiosity, is the CD drive totally dead?  Does it even try to read a CD/DVD on starting the computer?  Does the system BIOS see it?  Did you ever try making a pen drive copy of Ubuntu or FreeDos?

---


---
title: "Messed up boot sector and partition table!"
date: 2011-11-26
forum: General Help
---

### Post by cj_g0bl1n on 2011-11-26
I feel like a complete idiot.  Recently I've been developing an 8086 assembly game and decided I would test it on a sd card...  So I used dd...and instead of using /dev/sdb as the destination I used /dev/sda...  Which was my hard drive...  I was quite surprised when the sd card didn't boot up the game, and even more so when my hard drive booted it up!  The game is only 32 kb, so I must have overwrote the 32 kb on the hard drive.  I have a 250 GB hard drive and it would have used the default installation setup using Ubuntu 10.04 LTS.

Is there a to fix this?  The only way I can think of fixing this is to install ubuntu on another 250 GB hard drive and then issue dd again but this time the source being the new installation and the destination being the old one.  But if there is a better solution I am all ears!

---

### Post by LinuxFan999 on 2011-11-26
> **cj_g0bl1n said:**
> I feel like a complete idiot. Recently I've been developing an 8086 assembly game and decided I would test it on a sd card... So I used dd...and instead of using /dev/sdb as the destination I used /dev/sda... Which was my hard drive... I was quite surprised when the sd card didn't boot up the game, and even more so when my hard drive booted it up! The game is only 32 kb, so I must have overwrote the 32 kb on the hard drive. I have a 250 GB hard drive and it would have used the default installation setup using Ubuntu 10.04 LTS.
 
Is there a to fix this? **The only way I can think of fixing this is to install ubuntu on another 250 GB hard drive and then issue dd again but this time the source being the new installation and the destination being the old one.** But if there is a better solution I am all ears!
Why not just download andrn the Gparted Live CD, boot from it, make a new MBR, then boot from the Ubuntu CD and reinstall Ubuntu?

---

### Post by egalvan on 2011-11-26
Second, the boot sector & partition table are GONE (they reside in the first 512bytes),
if indeed you wrote 32KB to the hard drive.

First, STOP USING THE DRIVE. otherwise you risk overwriting more data.

getting the boot sector back is trivial... there are any number of "re-install grub" how-to's on the forum...

getting the partition table back is/may be trickier...

I suggest downloading PartedMagic LiveCD. it contains some excellent recovery tools, some specifically for partition table recovery.

Finally, getting the rest of the 31.5KB is gonna be the difficult/impossible part.
You actually removed files, and most likely a directory.
In this case your idea of re-installing on an identical drive may have merit...
assuming you do an IDENTICAL install...

then just use a disk editor to see whats on the first 31.5KB, and copy it over...

All-in-all, if you dont have much invested in the install, 
it MAY be easier ( and less time-consuming ) to re-install..

---

### Post by oldfred on 2011-11-26
When did you partition this? You did say KB not MB?

Older partitions started at sector 63, but new one's start at sector 2048 or 1MB. So only grub in the MBR, partition table in MBR and grub2's  core.img may have been overwritten.

Test disk may find old partitions, do you have any printouts or backups of partition table? I always keep a current results.txt from boot_info script after any changes just to have some of that type of info. 

Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2)
Grub2 info & full chroot version - also see METHOD 3 - CHROOT:
[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 and later with grub2) by talsemgeest
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by cj_g0bl1n on 2011-11-26
The only reason I do not reinstall Ubuntu is because there are files on the drive I want.  The first 32kb couldn't have been my files?  I know the first 512 bytes weren't (Grub stage 1, partition table, and finally 0xaa55 boot signature).  But the next 31.5 kb must have been something else, I wonder if the next chain linked boot loader was in the next 31.5 kb, if so that wouldn't be hard to change.  Sadly I do not have an identical drive, but I do have another 250 GB hard drive, but no two hard drives are exactly the same size.  Hopefully nothing super important was in the next 31.4 kb, like my crypto stuff!

EDIT:
I installed Ubuntu recently (last few months).  So I'm praying nothing important (by important I mean irreplaceable) was lost.  On the TestDisk website there are a billion options of what to download, would the [Ubuntu Rescue Remix]("http://ubuntu-rescue-remix.org/") do the job?

Edit 2:
So I ran the TestDisk utility, it recognized a primary linux partition, swap space partition, and a lba partition.  I wrote this to the partition table.  So I still do not have Grub, but I was hoping I could just mount the drive and get my files off of it (it's everything on my Desktop and in my Documents folder).  But when I do I get this:
"Error mounting: mount: Stale NFS file handle"
Any ideas?

---

### Post by oldfred on 2011-11-26
I have seen that before but do not have the solution in my notes. I think it was someone trying to run e2fsck and it did not work from Ubuntu as something was left open. One user was then able to run e2fsck from another liveCD. If you had encryption that is usually in that beginning of the drive and may be why it cannot see partition correctly.

This will not work if encrypted.
#From liveCD so everything is unmounted,swap off if necessary, change sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems.
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors:
sudo e2fsck -f -y -v /dev/sdb1

If not:
Problem running e2fsck apparently in use by the system,  Use Slitaz
[http://ubuntuforums.org/showthread.php?t=1713946](http://ubuntuforums.org/showthread.php?t=1713946)
SATA will use sda1 and IDE devices use hda1 in Slitaz

See also this thread:
[http://ubuntuforums.org/showthread.php?t=1684746](http://ubuntuforums.org/showthread.php?t=1684746)

---


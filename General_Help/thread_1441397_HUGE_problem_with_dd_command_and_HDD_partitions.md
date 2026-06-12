---
title: "HUGE problem with dd command and HDD partitions"
date: 2010-03-28
forum: General Help
---

### Post by mobio on 2010-03-28
This forum was always ultra helpful to me I hope it wont fail me now. 

I did something sutpid^nth degree. First most stupid things is that I am doing lot of different studies (including PhD) and I did not back up my data. Second is that I was helping my friend to restore his mybook world and his drive was mounted as sdb. My drive with all my data was mounted at sda. I logged as root using sudo -i.  My drive contains 4 partitions (IBM Lenovo rescue partiton, Kubuntu partition, Windows Vista, and FAT32 partition for exchange of data). 

Ok now what I did which was ultra mega stupid is that instead of typing 
dd if=rescue.img of=/dev/sdb I typed sda by accident so my whole partition table is gone now. Luckily however I did not restart my comp by this point so it is still seeing the whole HDD... So I realized what I did and copied most important files to external drive. At least my PhD which is almost written is saved (yeah stupid people get PhD) but now I would have to go trough hassle and reinstall a loads of software that I had on my windows drive in particular and I am kind of in the time creep. 

So before I pres restart and lose my hard drive is there any of the good people out who can advice me if I could make somehow disk image from my Windows partition from my Ubuntu (where I am now) and restore it later when I restore the partition table. One important thing to note is that if I start gparted it just see 120GB unallocated where my partitions were supposed to be. That is why (although not an expert) I doubt I can use something like partimage or similar. 
However since I still did not reboot my comp from the time of the accident I still can see all the files. Also in the meanwhile I managed to backup everything important so I am on the safe side now despite my stupidity but if there is a way that would save me few days and the re-installation of the system it would be great. 

Any advice is appreciable...

---

### Post by srs5694 on 2010-03-28
One critical question is: How big is the rescue.img file that you accidentally overwrote on /dev/sda? If it's sufficiently small (just 512 bytes, or at most perhaps 31KB or so), you may be able to recover your partitions with little or no data loss. If it was a big file, though, and if the dd operation completed, then anything on the hard disk up to the size of that image is gone.

If rescue.img was sufficiently small, one option is to use the testdisk utility to rediscover where your partitions are. This tool should be able to recreate your partition table and save the changes either before you shut down or in a subsequent recovery session.

Another option, if you haven't shut down, may be to extract the data from Linux's /proc and /sys virtual filesystems. I've never tried this under the circumstances you relate, but it may be worth trying:


[list=1]
[*]Print out a hardcopy of /proc/partitions. This file contains the major and minor device numbers and partition sizes (in kilobytes) associated with the partitions that are currently recognized by the kernel. (Major and minor numbers are used internally by the kernel to identify hardware devices. You'll use these shortly.) I *think* this information will remain unaffected by your inadvertent overwrite until you reboot, but I'm not positive of that. You're probably only interested in thesda* items.
[*]For each partition you want to recover (/dev/sda1 through /dev/sda{whatever}), examine the /sys/block/sda/sda{number}/start and /sys/block/sda/sda{number}/size files. (I'm assuming you only need to recover /dev/sda; change as necessary.) For instance, you'd examine /sys/block/sda/sda1/start and /sys/block/sda/sda1/size to obtain information on /dev/sda1. These files hold the starting sector number and size (in sectors) of the partition. Write these values down on the printout you made.
[*]For each partition, compute a new ending sector number. This will be the length *in sectors* (either from the size file or twice the size in kilobytes from /proc/partitions) plus the start sector minus 1. For instance, if you find a start sector of 34 and a size of 390592, the end point is (390592 + 34 - 1 = 390625). Write this value down on your printout.
[*]If your disk had logical partitions, the extended partition that housed them will have a very short size value. I'm seeing values of 1 or 2 sectors on my test disks. Its start sector will be a few sectors (1-63, probably) prior to the first logical partition. Make note of this extended partition, if present.
[*]Now fire up fdisk: Type "sudo fdisk /dev/sda".
[*]In fdisk, type "u" to change the units to sectors.
[*]In fdisk, type "o" to create a fresh partition table (the old one is rubbish).
[*]In fdisk, use the "n" command to create new partitions that match the originals in start sector and size. You'll have to understand how extended partitions enclose all logical partitions to create a proper extended partition; you'll ignore its size value and create a partition of the appropriate size. Logical partitions reside inside the extended partition. Use the "t" command to change partitions' type codes to suitable values.
[*]When you're done, type "p" to examine your partitions. If they seem sensible, proceed. If fdisk complained about overlapping partitions when you tried to create them, you probably erred in your computations or in writing down some values. Go back and review them.
[*]When you're done, type "w" to save your changes.
[*]Reboot and hope for the best.
[/list]


With luck, your partitions will now be restored; however, if rescue.img was big enough to overwrite even part of one or more partitions, their contents are now corrupted. Filesystem recovery utilities such as fsck (for Linux filesystems) or CHKDSK (for FAT or NTFS in Windows) might be able to help, but this is far from guaranteed.

Good luck!

---

### Post by mobio on 2010-03-29
I am deeply grateful for your reply. Thank you !
 
Unfortunately rescue.img was 51 MB so I guess there is not much I can do with testdisk. To continue my streak of bad luck, for some reason Kubuntu crashed while installing testdisk, so I guess there is not much I could do now regarding the described steps. 

On the bright side however I managed to access the drive using partimage, before it crashed and to create a rescue image of my ntfs (Windows) partition. One thing to note is that when I acessed my hdd with partimage sda1 was unallocated (do not have clue what was there but maybe lenovo rescue thing) than sda2 (Windows) seemed ok. Now when I reboot the comp as expected it behaves like hdd is not there since everything is seen as unallocated space. For some reason also ubuntu live CD does not work (I guess it needs some hdd space).


 So continuing my question is there a way to force restore the partition from the image file in to the new partition table?

What I plane to do is to make some bootable USB with like parted magic on it and recreate new partition table and reformat partitions. Than the question is could I create new ntfs partition and just restore content of my HDD saved in the image file and get functional Windows system and programs back?

---

### Post by srs5694 on 2010-03-29
51MB is small enough that it's probably only wiped out your first partition; testdisk, run from a PartedMagic or System Rescue CD disc (if either has it; I've not checked) should be able to recover any partitions *after* the 51MB point on the disk. Thus, I recommend you try that first.

At that point, you may have free space that used to be your first partition. You can try restoring that from your backup, if that's what you backed up; however, that backup will almost certainly be corrupt. You may be able to repair it with fsck or CHKDSK, but I wouldn't get my hopes up about that. Chances are it's just plain gone.

---


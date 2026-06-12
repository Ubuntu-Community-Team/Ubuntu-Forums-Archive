---
title: "Gparted questions re: merging partitions"
date: 2010-05-06
forum: General Help
---

### Post by quadproc on 2010-05-06
Someone who knows the design behind gparted can probably answer this question for me: I would like to merge two partitions into one.  Right now one of them is formatted ntfs and the other is ext3.  Since I have no use for the ntfs stuff (except for the boot sector), I would like to change it to ext3 and merge it with the adjacent ext3 partition.

If I try to do this by reformatting the ntfs partition to ext3, would the two partitions become one?  If not, then can I delete the old ntfs partition and then grow the ext3 partition into the freed space?  What would happen to the boot information?

A little background information might help the reader to understand why I am doing this.  When I ordered this system I wanted the vendor to check out the hardware before shipping it.  The only "tool" that they had for that purpose was Windows Vista.  I had no interest in Windows anything but I did want the vendor to check things out so I had them install Vista on it.  I think that I used it twice, once to see if it would run and, later, once to look up some system characteristic.  At the second Vista boot, it announced that it was "fixing" a problem on my hard disk and it did not give me a chance to say no.  I quickly killed that session.   When I logged back in to Ubuntu, fsck found damage to the boot disk and was fortunately able to repair it.  That's how I ended up with an ntfs partition located smack dab in the middle of prime territory.

Originally, /dev/sdc was also dedicated to Vista but it a simple matter to change it over to ext3 and automount it.  But it does still seem to have some vestiges of its original setup.

If you have read this far then you may be able to help so I will include some snippets from the boot_info_script.

> ============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #7 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No boot loader is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda8: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   
=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb46582ba

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   284,655,734   284,653,687   7 HPFS/NTFS
/dev/sda2         284,655,735 1,953,520,064 1,668,864,330   5 Extended
/dev/sda5         284,655,798   636,222,194   351,566,397  83 Linux
/dev/sda6       1,935,334,548 1,953,520,064    18,185,517  82 Linux swap / Solaris
/dev/sda7         636,222,258 1,899,525,599 1,263,303,342  83 Linux
/dev/sda8       1,899,525,663 1,935,334,484    35,808,822  82 Linux swap / Solaris

(much deleted material)

=================== sda7: Location of files loaded by Grub: ===================


 853.3GB: boot/grub/menu.lst
 853.2GB: boot/grub/stage2
 853.2GB: boot/initrd.img-2.6.28-18-generic
 853.3GB: boot/initrd.img-2.6.31-20-generic
 853.2GB: boot/vmlinuz-2.6.28-18-generic
 853.3GB: boot/vmlinuz-2.6.31-20-generic
 853.3GB: initrd.img
 853.2GB: initrd.img.old
 853.3GB: vmlinuz
 853.2GB: vmlinuz.old
Thanks for your help.

quadproc

---

### Post by dcstar on 2010-05-07
> **quadproc said:**
> Someone who knows the design behind gparted can probably answer this question for me: I would like to merge two partitions into one.  Right now one of them is formatted ntfs and the other is ext3.  Since I have no use for the ntfs stuff (except for the boot sector), I would like to change it to ext3 and merge it with the adjacent ext3 partition.

If I try to do this by reformatting the ntfs partition to ext3, would the two partitions become one?  If not, then can I delete the old ntfs partition and then grow the ext3 partition into the freed space?  What would happen to the boot information?
........

You cannot "merge" partitions. You can only grow partitions into unused space.

If you delete a partition that holds a bootloader, then you must reinstall whatever bootloader you use into another partition.

---

### Post by jbrown96 on 2010-05-07
Sorry but you won't be able to merge those partitions. 
Partition tables can only support four physical partitions. However, disks support more than that through the use of logical partitions. You can only merge partitions that are adjacent, and while I can't tell if you are trying to merge /dev/sda1 with /dev/sda5 or /dev/sda7, they are not adjacent. You will have to backup your data and alter your partition table. 

That looks like a good idea anyway. Why do you have two swap partitions on the same disk? That's completely unnecessary and highly unrecommended. 

Even if the partitions were adjacent, then you would need to have the ext3 one first, or else it gets really complicated.

---

### Post by quadproc on 2010-05-07
> **jbrown96 said:**
> Sorry but you won't be able to merge those partitions. 
Partition tables can only support four physical partitions. However, disks support more than that through the use of logical partitions. You can only merge partitions that are adjacent, and while I can't tell if you are trying to merge /dev/sda1 with /dev/sda5 or /dev/sda7, they are not adjacent. You will have to backup your data and alter your partition table. 

Fortunately, data is not an issue because it lives on a different drive and partition.

What I would like to do is to reclaim the space that the present /dev/sda1 partition is using.  I plan to add another partition and to resize the sda5 and sda7 partitions in the near future.
> 
That looks like a good idea anyway. Why do you have two swap partitions on the same disk? That's completely unnecessary and highly unrecommended. 
The two swap partitions were a result of upgrading 9.04 to 9.10.  I don't know why the update software did that.> 
Even if the partitions were adjacent, then you would need to have the ext3 one first, or else it gets really complicated.Accoring to fdisk, my partitions are arranged this way right now where # indicates juxtaposition:
(starting at 1) sda1#sda2 (to end of disk)
Within the sda2 partition are four logical partitions:
(starting at start of sda2) sda5#sda7 (large unassigned gap) sda8#sda6 (end of disk)

Things are somewhat helter skelter as a result of having removed some old partitions.

I think that I should reformat sda1 to be ext3, then move the boundary between sda1 and sda2 to allow for the desired 120GB in sda1, then move sda5 and sda7 to the start of sda2.  Finally, figure out how to use a single sda6 partition for any and all OS partitions.  Your thoughts, please?

Thanks for your help.

quadproc

---

### Post by jbrown96 on 2010-05-07
Sorry I didn't read the partition boundries that closely. I still don't think it will work though. /dev/sda2 is not a real partition. It's a logical partition. It's a piece of information that allows you to use all the partitions past #4. You won't be able to merge any primary with logical partitions because /dev/sda2 will always be in the way. 

1)
That being said, there is a way to do it, provided that /dev/sda1 is larger than the used space in /dev/sda5 and/or /dev/sda7. You can setup a LVM that takes several partitions (or disks) and merges them into one virtual partition. This is complicated and will hamstring you from moving partitions around in the future, and even worse, fixing Grub will be a pain. I can help you do this if you want.

2) 
You can backup all your data to another disk and wipe your drive and get back to a sane partitioning setup. This is, by far, the best way to do it. I would still recommend setting up an LVM during the re-install because it will give you flexibility if you want to re-partition or expand your disk space in the future. 

If you still really want to try to merge the partitions, then it would be really nice to attach a screenshot of your disk from gparted. It's just not easy to look at those start/stop sectors and know what's going on.

---

### Post by quadproc on 2010-05-07
> **jbrown96 said:**
> ...
1)
That being said, there is a way to do it, provided that /dev/sda1 is larger than the used space in /dev/sda5 and/or /dev/sda7. You can setup a LVM that takes several partitions (or disks) and merges them into one virtual partition. This is complicated and will hamstring you from moving partitions around in the future, and even worse, fixing Grub will be a pain. I can help you do this if you want.
I was hoping to simplify future changes so I think that I had better not go this way.  Also, I hadn't mentioned it previously, but I am going to need to visit the grub issue when I install a new partition.> 

2) 
You can backup all your data to another disk and wipe your drive and get back to a sane partitioning setup. This is, by far, the best way to do it. I would still recommend setting up an LVM during the re-install because it will give you flexibility if you want to re-partition or expand your disk space in the future. 
The data is already living on a completely separate drive and partition so that should not be an issue.  I do have a major concern, though: I would like to avoid having to redo all of the package installations, configuration settings, and system customizations which I now have.  This means that I want to avoid doing a reinstall.> 
If you still really want to try to merge the partitions, then it would be really nice to attach a screenshot of your disk from gparted. It's just not easy to look at those start/stop sectors and know what's going on.I was going to attach a screenshot but I can't find the file that it should have created.  I will keep trying and will try to add it if possible.

quadproc

---

### Post by jbrown96 on 2010-05-07
If you have an external disk with enough disk space to backup your Ubuntu install, then you won't need to reinstall at all. A simple copy operation will back everything up, and then you can use the LiveCD/USB to repartition, restore, and fix grub. 

Post ```
mount -l
``` and I get back with the rest of the instructions. 
What's on /dev/sda5 and /dev/sda7 (mount -l should clarify)?

---

### Post by quadproc on 2010-05-07
> **jbrown96 said:**
> If you have an external disk with enough disk space to backup your Ubuntu install, then you won't need to reinstall at all. A simple copy operation will back everything up, and then you can use the LiveCD/USB to repartition, restore, and fix grub. 

Post ```
mount -l
``` and I get back with the rest of the instructions. 
What's on /dev/sda5 and /dev/sda7 (mount -l should clarify)?
> mount -l
/dev/sda7 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/dev/sdc1 on /home type ext3 (rw,relatime,errors=remount-ro)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/bob/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=bob)

At present, sda5 has Ubuntu 8.10 and some /home stuff related to that, and sda7 has Ubuntu 9.10 (plus the remnants of 9.04 which no longer function properly).

I just checked my external disk and it has about 250GB available in its only partition.  The sda5 and sda7 partitions together add up to about 24GB so they will easily fit.

quadproc

---

### Post by srs5694 on 2010-05-07
I think this thread is suffering badly from a lack of basic information.

First, quadproc, I think you need to say precisely what's on some of your /dev/sdb and /dev/sdc partitions. You've got ext3 filesystems on both, and it's not clear how your partitions all fit together or what their relative sizes are. For instance, do you have a separate /home partition? Perhaps posting the output of "df -h" would help us see how your system is put together. If some partitions aren't always mounted, mount them before using the "df -h" command. If some partitions don't show up, be sure to tell us how big they are. (The output of "sudo fdisk -lu" can help. Be sure to post it between [noparse]```
[/noparse] and [noparse]
```[/noparse] tags for legibility.)

I also disagree with some of jbrown96's comments:

[quote=jbrown96]Even if the partitions were adjacent, then you would need to have the ext3 one first[/quote]

I'm not sure where this is coming from. Given that /dev/sda1 is NTFS and /dev/sda5 (the next filesystem-containing partition) is ext3fs, and given no need to preserve data in /dev/sda1, it's a simple matter to delete /dev/sda1, expand the /dev/sda2 extended partition to the left, and expand /dev/sda5 to the left -- at least, it's simple in terms of the operations within an emergency disc's GParted. The operations are likely to take a while to work.

That said, I'm not sure that doing this would provide much benefit.

[quote=jbrown96]/dev/sda2 is not a real partition. It's a logical partition. It's a piece of information that allows you to use all the partitions past #4.[/quote]

This is conceptually correct, but the correct name for /dev/sda2 is *extended* partition. An extended partition holds logical partitions.

[quote=jbrown96]You can setup a LVM that takes several partitions (or disks) and merges them into one virtual partition. This is complicated and will hamstring you from moving partitions around in the future, and even worse, fixing Grub will be a pain.[/quote]

An LVM is certainly an option, and it can be complicated to set up; but I disagree with the assessment that it "hamstrings" future adjustments. The whole point of an LVM is to enable *easier* and *more flexible* adjustments. With an LVM, filesystems are stored in structures known as logical volumes, which you can treat much like files in a filesystem. That is, you don't need to worry about where they begin or end, or how much space exists between individual logical volumes. You can add them, delete them, or resize them and the LVM utilities take care of the details. The only way in which an LVM can be said to "hamstring" future adjustments is in how Linux interacts with other OSes, and even that's no worse than a non-LVM configuration. GRUB configuration also isn't particularly complex. All that said, converting from a non-LVM to an LVM configuration can be complex.

Overall, it's unclear to me precisely what your setup is, quadproc, or what your goal state is. Certainly you've got some inefficient partition layouts at the moment, so big changes are in order. I strongly suspect that achieving a likely goal state will entail either re-installing the OS or backing it up, repartitioning, and restoring. An LVM might or might not be useful or desirable. I've found that when systems get like that, the best course of action is often to wipe out the entire partitioning system and start from scratch; however, a series of incremental changes can sometimes work as well.

---

### Post by quadproc on 2010-05-07
> **srs5694 said:**
> I think this thread is suffering badly from a lack of basic information.

First, quadproc, I think you need to say precisely what's on some of your /dev/sdb and /dev/sdc partitions. You've got ext3 filesystems on both, and it's not clear how your partitions all fit together or what their relative sizes are. For instance, do you have a separate /home partition? Yes, sdc has one 140 GB partition which holds /home.  This is a high speed disk as opposed to the others which are standard speed.
> Perhaps posting the output of "df -h" would help us see how your system is put together. If some partitions aren't always mounted, mount them before using the "df -h" command. If some partitions don't show up, be sure to tell us how big they are.OK, here is df -h output obtained with the system in nominal configuration.  the system could have a different disk where sdh is, and it could have USB flash drives on it, and it could have a floppy or a CDROM on it at various times.
```
df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda7             119G   16G   97G  14% /
udev                  3.0G  376K  3.0G   1% /dev
none                  3.0G  272K  3.0G   1% /dev/shm
none                  3.0G  104K  3.0G   1% /var/run
none                  3.0G  4.0K  3.0G   1% /var/lock
none                  3.0G     0  3.0G   0% /lib/init/rw
/dev/sdc1             138G  6.6G  125G   5% /home
/dev/sdh1             289G   13G  262G   5% /y

```>  (The output of "sudo fdisk -lu" can help. Be sure to post it between [noparse]```
[/noparse] and [noparse]
```[/noparse] tags for legibility.)OK, I hope that I get the formatting right.
[noparse]
sudo fdisk -lu

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb46582ba

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   284655734   142326843+   7  HPFS/NTFS
/dev/sda2       284655735  1953520064   834432165    5  Extended
/dev/sda5       284655798   636222194   175783198+  83  Linux
/dev/sda6      1935334548  1953520064     9092758+  82  Linux swap / Solaris
/dev/sda7       636222258   888121394   125949568+  83  Linux
/dev/sda8      1909743003  1935334484    12795741   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdc: 150.0 GB, 150039945216 bytes
255 heads, 63 sectors/track, 18241 cylinders, total 293046768 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb46582be

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1              63   293041664   146520801   83  Linux

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000b4931

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63  1629762119   814881028+   5  Extended
/dev/sdb5             126  1233695609   616847742   83  Linux
/dev/sdb6      1233695673  1268653049    17478688+  82  Linux swap / Solaris

Disk /dev/sdh: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000a23aa

   Device Boot      Start         End      Blocks   Id  System
/dev/sdh1              63   614405924   307202931   83  Linux

 [/noparse]
> 
I also disagree with some of jbrown96's comments:

I'm not sure where this is coming from. Given that /dev/sda1 is NTFS and /dev/sda5 (the next filesystem-containing partition) is ext3fs, and given no need to preserve data in /dev/sda1, it's a simple matter to delete /dev/sda1, expand the /dev/sda2 extended partition to the left, and expand /dev/sda5 to the left -- at least, it's simple in terms of the operations within an emergency disc's GParted. The operations are likely to take a while to work.

That said, I'm not sure that doing this would provide much benefit.A good observation.  My main reason for keeping the version 8.10 stuff is that it is a fallback in case of major system problems.  I had to use it after installing 9.04 because 9.04 broke this system so badly that I spent two very long days just getting it back to where I had a command line capability.  There are a couple of other reasons but suffice it to say that I don't want to lose this version.> 

This is conceptually correct, but the correct name for /dev/sda2 is *extended* partition. An extended partition holds logical partitions.

(LVM discussion omitted)

Overall, it's unclear to me precisely what your setup is, quadproc, or what your goal state is. Certainly you've got some inefficient partition layouts at the moment, so big changes are in order. I strongly suspect that achieving a likely goal state will entail either re-installing the OS or backing it up, repartitioning, and restoring. An LVM might or might not be useful or desirable. I've found that when systems get like that, the best course of action is often to wipe out the entire partitioning system and start from scratch; however, a series of incremental changes can sometimes work as well.I have been taking the incremental approach because I prefer to know what change broke the system if there is trouble.

Here is a summary of the system disk hardware:
sda: 1TB main disk
sdb: 1TB which I would like to use as RAID 1 in conjunction with sda (presently empty)
sdc: 140GB for data
sdh: removable disk of various sizes, UUIDs, and content; usually a backup disk

Here is a summary of what I would like to have in software:
8.10 in its own partition including a /home local to it
9.04 in its own partition using /home from sdc
9.10 in its own partition using /home from sdc
future OS, probably 10.04.1 in its own partition using /home from sdc
a swap partition of at least 12.2GB; can be shared by all

Back to RAID for a moment: my mother board claims to have RAID capability but the manual says virtually nothing other than "enable it here".  I have not been able to get a more definitive answer from the manufacturer.  So I am thinking that software RAID would be appropriate.

This posting is getting to be long; I hope that I have provided insight into the setup.  Please ask if anything is unclear.

On a loosely related note: why does gparted _copy_ the contents of a swap partition?  Why not just trash it and replace it with a new one?

Thanks for all your help.

quadproc

---

### Post by srs5694 on 2010-05-07
That was very helpful. Trivia first: You got the [noparse]```

```[/noparse] formatting correct for the "df -h" output, but not for the "sudo fdisk -lu" output.

My first observation is that your /dev/sda7 root (/) partition is ridiculously oversized -- it's 119GB in size, but you're using just 16GB of it. 16GB is actually pretty big for an Ubuntu installation, so I'll deviate from my usual "5-20GB" recommendation in your case and say "20-30GB," unless you peruse it and find a lot of wasted disk space somewhere. Given the below, even 35GB might be OK....

I'm not sure of the value of using RAID 1 mirroring for your basic installations; most system software is easily replaced, so the RAID 1 mirroring will take a lot of effort to set up with very little saved effort if a disk should fail. User data, OTOH, is hard to generate and more valuable; that makes more sense to protect with RAID 1. Therefore, I'd recommend doing this: Set up your three or four Linux installations on your 140GB /dev/sdc (that gives about 35GB apiece, which is plenty; or you could vary it a bit to give more space to your install with its own /home partition), then set up RAID 1 on your two 1TB disks and put /home on them. That'll give you plenty of space for user files in /home. I'd also put swap on the two 1TB disks, but I'd use RAID 0 for them. (I'm pretty sure you can mix-and-match RAID types when using software RAID, but I'm a little rusty on this.) That way, you'll get a bit of a speed boost on your swap space. Each 1TB disk will therefore have two RAID partition, one big and one small.

Here, in outline, is the procedure to set this up:


[list=1]
[*]Use GParted to shrink /dev/sdc1 so that it's the size of one of the planned Linux root partitions (~35GB if you give them all equal space, or more or less than this if you want to give them unequal spaces). Ideally, /dev/sdc1 will ultimately be your future 10.04.1 installation, so that you won't need to overwrite it immediately.
[*]Create three additional partitions on /dev/sdc, to hold your 8.04, 9.04, and 9.10 installations. I'd make them logical partitions for maximum future flexibility, but they could be primaries.
[*]Transfer your installations from /dev/sda7 and elsewhere to the empty /dev/sdc partitions. There are a number of backup tools you can use for this. For instance, if you want to use tar, you could mount the source at /mnt/source and the destination at /mnt/dest, then cd into /mnt/source and type "sudo tar cpf - --one-file-system ./ | (cd /mnt/dest; sudo tar xvpf -)". (This works for either the currently booted system or another system, but of course you'd cd to / if you were copying the current system.) You'll then need to edit the copied system's /etc/fstab file to update the UUID for the root (/) filesystem. Edit whatever GRUB installation is active for the change and test the boot after each system copy.
[*]At this point, all your current Linux installations should be duplicated and bootable from /dev/sdc. You can therefore terminate use of swap ("sudo swapoff -a" to do it temporarily; edit /etc/fstab to do it permanently) and repartition /dev/sda with two RAID partitions (MBR type code 0xfd, if you stick with MBR), one small for swap and the other big for /home. Continue configuring RAID; consult an appropriate online tutorial for details.
[*]Set up the RAID swap space using mkswap and swapon, and edit your /etc/fstab files appropriately.
[*]Set up the RAID /home partition and copy your current /home directory there, using the same tar command described earlier (but with changed directory mount points, of course).
[*]Edit your /etc/fstab files to mount the new RAIDed /home instead of the current home.
[*]Reboot into each system to verify that it's using the new RAIDed home. Satisfy yourself that all the files are present. (Take your time; wait days or weeks, if you like.)
[*]Delete the original /home files from /dev/sdc1. (You can just create a fresh filesystem on /dev/sdc1, if you like.) You may now re-use this partition for your final OS install.
[/list]


This procedure is a bit lengthy, but with the exception of resizing /dev/sdc1, no single step is very dangerous (and even resizing /dev/sdc1 isn't all *that* dangerous; but backing it up first is a sensible precaution). The end result should be something that's much neater than what you've got now.

Oh, and the last I heard, the RAID support on most motherboards was virtually useless in Linux, so you're right to plan on using Linux's variety of software RAID.

---

### Post by quadproc on 2010-05-08
> **srs5694 said:**
> That was very helpful. Trivia first: You got the [noparse]```

```[/noparse] formatting correct for the "df -h" output, but not for the "sudo fdisk -lu" output.

My first observation is that your /dev/sda7 root (/) partition is ridiculously oversized -- it's 119GB in size, but you're using just 16GB of it. 16GB is actually pretty big for an Ubuntu installation, so I'll deviate from my usual "5-20GB" recommendation in your case and say "20-30GB," unless you peruse it and find a lot of wasted disk space somewhere. Given the below, even 35GB might be OK....
Regarding partition sizes, about a decade ago I was growing file systems at the rate of about 10 GB per year.  I figure that this rate of growth is probably accelerating and is probably around 20 GB/year for me and the way that I do things at the present time. Looking in Synaptic I find that I only have about 5% of the available packages installed; granted, many of these are quite small but I really don't want to get into a situation where I am running out of disk (I have been burned by this issue more than once).  Given that disks are large these days I wanted to be sure to have plenty of space available in each partition so I settled on 120GB each figuring that software will grow to fit the available space when given the chance, and figuring that I could have more than  four "slots" for operating systems (at least three in use and one for transitions to new releases).

(recommendations elided)

Very good.  You have given me a lot to consider; I will save this posting for reference as I plan what to do.

Thank you for your useful and insightful responses.

EDIT:
I just wanted to add one observation about another problem that I encountered in the process of converting sdc to ext3.  I started to notice BIOS error messages at startup time along the lines of "Express Gate installation is incomplete"  but the system starts and runs OK.  Express Gate is a "feature" on most ASUS motherboards which provides a mini OS as part of the BIOS and allows the user to access things such as Skype or a browser without doing a normal boot.  After researching this error message I now know that many ASUS motherboards put that Express Gate functionality on your disk, not on the motherboard!  Apparently, the BIOS is looking on sdc for Express Gate and cannot find it.  Now I am concerned that the BIOS might have hooks into the ntfs partition on sda.  Comments, please?

quadproc

---

### Post by quadproc on 2010-05-08
Please see last paragraph of previous post.  Thanks.

quadproc

---


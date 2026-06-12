---
title: "64bit Lucid (ugraded from Hardy) hangs on boot"
date: 2010-07-06
forum: General Help
---

### Post by which_chick on 2010-07-06
Computer is a Dell Inspiron 1520, stable, was running 64-bit Hardy 8.04 nicely until I upgraded it last night to 64-bit Lucid 10.04 via the instructions here:  [https://help.ubuntu.com/community/LucidUpgrades](https://help.ubuntu.com/community/LucidUpgrades) (the "hit alt-f2, type in stuff" directions for 8.04 Hardy people.  Seemed to go OK despite taking a couple of hours.)

When I went to reboot the system after the upgrade, it came up to the purple Ubuntu screen with the five or six dots and the following error message:

"An error occurred while mounting uuid dd014eae-45ab-4971-b5b2-6943acd99c5c

Press S to Skip, M for Manual."

I press S and the system boots fine.

I did not have this problem under 8.04 Hardy.  This system originally dual booted XP and 8.04 Hardy but about two years ago, XP died for no apparent reason and I let it.  It does not need to boot into XP ever again but I still have the partition because I have a bunch of stuff stored there that I don't want to sort through.

Here's some stuff that might be useful...

```
jessica@RedLaptop:~$ sudo parted -l
Model: ATA SAMSUNG HM320JI (scsi)
Disk /dev/sda: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 2      32.9MB  76.2GB  76.2GB  primary   ntfs            boot
 1      76.2GB  133GB   57.1GB  primary   ext3
 4      133GB   189GB   56.2GB  primary   ext3
 3      189GB   316GB   126GB   extended                  lba
 5      189GB   308GB   119GB   logical   ext3            boot
 6      308GB   313GB   5075MB  logical   linux-swap(v1)

jessica@RedLaptop:~$ sudo blkid
/dev/sda1: UUID="641d9ed7-8906-4739-b3ed-6098a51844e0" TYPE="ext3" 
/dev/sda2: UUID="043C708A3C70790E" TYPE="ntfs" 
/dev/sda4: UUID="8128b883-b15c-4355-888f-53592374e5f4" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="ea097450-6c32-4f5d-89d2-ec238d21db48" TYPE="ext3" 
/dev/sda6: UUID="dd014eae-45ab-4971-b5b2-6943acd99c5c" TYPE="swap" 

jessica@RedLaptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda5 UUID=ea097450-6c32-4f5d-89d2-ec238d21db48 /               ext3    defaults,errors=remount-ro 0       1
/dev/sda6 UUID=dd014eae-45ab-4971-b5b2-6943acd99c5c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/sda2 /windows ntfs auto,ro,users 0 0
/dev/sda1  /home/jessica/Music ext3 user,rw,nosuid,nodev,exec,async 0 0

jessica@RedLaptop:~$ sudo mount -a
[mntent]: line 5 in /etc/fstab is bad
[mntent]: line 6 in /etc/fstab is bad

root@RedLaptop:~# fdisk -lu

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x41ab2316

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1       148810095   260285129    55737517+  83  Linux
/dev/sda2   *       64260   148810094    74372917+   7  HPFS/NTFS
/dev/sda3       369993015   616944194   123475590    f  W95 Ext'd (LBA)
/dev/sda4       260285130   369993014    54853942+  83  Linux
/dev/sda5   *   369993141   601794899   115900879+  83  Linux
/dev/sda6       601794963   611707004     4956021   82  Linux swap / Solaris

Partition table entries are not in disk order

root@RedLaptop:~# mount
/dev/sda5 on / type ext3 (rw)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/dev/sda2 on /windows type fuseblk (ro,noexec,nosuid,nodev,allow_other,blksize=4096)
/dev/sda1 on /home/jessica/Music type ext3 (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/jessica/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=jessica)

jessica@RedLaptop:~$ df -m
Filesystem           1M-blocks      Used Available Use% Mounted on
/dev/sda5               111408     94774     10975  90% /
none                      1505         1      1505   1% /dev
none                      1510         2      1508   1% /dev/shm
none                      1510         1      1509   1% /var/run
none                      1510         0      1510   0% /var/lock
none                      1510         0      1510   0% /lib/init/rw
/dev/sda2                72630     66491      6139  92% /windows
/dev/sda1                53576     15743     35112  31% /home/jessica/Music

```
I'm not super clueful, but it looks like it's not mounting the swap partition.  The UUID for the swap partition matches the UUID in the error message.

Looking at this in the Disc Utility under System-Administration, it's like this:

/dev/sda1 mounts at /home/jessica/Music

/dev/sda2 is mounted as /windows in the filesystem.  It contains what's left of WindowsXP, notably my *other* mp3 files that I haven't moved or sorted and also old pictures and stuff.

/dev/sda3 is a placeholder for logical partitions that contains two sub-partitions:
     /dev/sda4, which is mounted on /media/blahblah right now
     /dev/sda6, which is the swap partition, NOT MOUNTED

/dev/sda5 is mounted as / on the linux filesystem)

So, the question here is this:  How do I fix my system so that I do not have to hit "S" to boot it?  (If you need or would like more information or output, please let me know.)

Thanks for any advice you can offer!

Edit:  Leppie offered the correct answer, which is "You can use EITHER UUID or /dev/sdwhatever to refer to a partition in /etc/fstab, but not both for the same entry" after I found it out by trial and success via careful editing of /etc/fstab.  Still not sure how it got that way, but once I straightened out /etc/fstab to just have the /dev/whatevers, it worked fine.

---

### Post by Leppie on 2010-07-06
in gparted, delete the swap and then recreate it.
you can then get the UUID, which probably is the same as it is now, with the blkid command. then copy and paste into /etc/fstab to replace the old swap's UUID

---

### Post by which_chick on 2010-07-06
> **Leppie said:**
> in gparted, delete the swap and then recreate it.
you can then get the UUID, which probably is the same as it is now, with the blkid command. then copy and paste into /etc/fstab to replace the old swap's UUID

Okay, I did like you said.  I got a slightly different UUID but that's probably because I drug the slider a different distance or something.  I put the new UUID into /etc/fstab and saved and rebooted.

I took better notes this time upon reboot.  There are actually *two* "Press S to Skip" messages, with different UUIDs to 'em.

The first message is all "ea097450-6c32-4f5d-89d2-ec238d21db48" which is the /dev/hda5 which mounts as / for linux.

The second message is (now) "542620bc-0f6504d4cb1d7-487f2e0cd325" which is the /dev/hda6 which is supposed to mount as swap for linux.

The reason I didn't see this earlier was that apparently I press-n-hold the "S" key when irritated and that counts as two "S" presses.  When I slowed down to take better notes, I finally saw the two different error messages.  There's also something that flashes white in the upper left hand corner *BEFORE* the Ubuntu screen with the dots but it's gone too quickly for me to see it.

Since the uuid for swap changed, here's another look at some output:

```
jessica@RedLaptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda5 UUID=ea097450-6c32-4f5d-89d2-ec238d21db48 /               ext3    defaults,errors=remount-ro 0       1
/dev/sda6 UUID=542620bc-0f65-4d5c-b1d7-487f2e0cd325 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/sda2 /windows ntfs auto,ro,users 0 0
/dev/sda1  /home/jessica/Music ext3 user,rw,nosuid,nodev,exec,async 0 0

jessica@RedLaptop:~$ sudo mount -a
[mntent]: line 5 in /etc/fstab is bad
[mntent]: line 6 in /etc/fstab is bad

jessica@RedLaptop:~$ sudo blkid
/dev/sda1: UUID="641d9ed7-8906-4739-b3ed-6098a51844e0" TYPE="ext3" 
/dev/sda2: UUID="043C708A3C70790E" TYPE="ntfs" 
/dev/sda4: UUID="8128b883-b15c-4355-888f-53592374e5f4" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="ea097450-6c32-4f5d-89d2-ec238d21db48" TYPE="ext3" 
/dev/sda6: UUID="542620bc-0f65-4d5c-b1d7-487f2e0cd325" TYPE="swap" 

jessica@RedLaptop:~$ mount -l
/dev/sda5 on / type ext3 (rw)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/dev/sda2 on /windows type fuseblk (ro,noexec,nosuid,nodev,allow_other,blksize=4096)
/dev/sda1 on /home/jessica/Music type ext3 (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/jessica/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=jessica)

```

Interestingly, the system works OK if I go on to press S twice.  I am typing to you on it now.

Is the fstab formatting OK?  How does the /dev/hda5 get mounted when I'm pressing "S" to Skip?  What's up with that?

Does the fact that both of the partitions that are throwing crap errors live on a W95 Ext'd (LBA) partition (/dev/hda3 is a placeholder for the logical partitions /dev/hda5 and /dev/hda6) make any difference?

Any more ideas?

---

### Post by which_chick on 2010-07-07
I think I have this work-arounded for the moment, but anyone able to explain a proper fix and/or how things got wrong in the first place would still be very much appreciated.

But anyway.  So I tried the following:

```
jessica@RedLaptop:~$ sudo mkswap /dev/sda6
[sudo] password for jessica: 
Setting up swapspace version 1, size = 7574612 KiB
no label, UUID=60668a67-6b9a-410a-97b9-46e7a03a5d03

```

(The partition was already /dev/sda6 so I figured I would see if it would turn on as swap.  Manually.)

```
jessica@RedLaptop:~$ sudo swapon /dev/sda6

jessica@RedLaptop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          3018       1143       1874          0        126        384
-/+ buffers/cache:        632       2385
Swap:         7397          0       7397

```

Yep, it did.

```
jessica@RedLaptop:~$ sudo blkid
/dev/sda1: UUID="641d9ed7-8906-4739-b3ed-6098a51844e0" TYPE="ext3" 
/dev/sda2: UUID="043C708A3C70790E" TYPE="ntfs" 
/dev/sda4: UUID="8128b883-b15c-4355-888f-53592374e5f4" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="ea097450-6c32-4f5d-89d2-ec238d21db48" TYPE="ext3" 
/dev/sda6: UUID="60668a67-6b9a-410a-97b9-46e7a03a5d03" TYPE="swap" 

```

But here the UUID is different.  I don't get that, but whatever.

```
jessica@RedLaptop:~$ sudo swapoff /dev/sda6
jessica@RedLaptop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          3018       1135       1882          0        127        384
-/+ buffers/cache:        623       2394
Swap:            0          0          0

```

And it turns off, too.

So, I figured that the problem was not with the partition or with swap as a concept.

Then, I went to look at boot errors.  They said something about not able to locate UUID whatever.  

I edited fstab to remove the swap uuid (because I figured it booted anyway with messed-up swap partition information).

It worked better (only one error, not two).
I edited fstab to remove the /dev/sda5 uuid.

It ran fsck and then booted without error.  I'm shutting it down now for the night...

Not sure what went wrong there, but it did not like the UUIDs at all.  Current fstab looks like this:

```
jessica@RedLaptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda5  /               ext3    defaults,errors=remount-ro 0       1
/dev/sda6 none swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/sda2 /windows ntfs auto,ro,users 0 0
/dev/sda1  /home/jessica/Music ext3 user,rw,nosuid,nodev,exec,async 0 0

```

And how's that work?

```
jessica@RedLaptop:~$ sudo mount -a
jessica@RedLaptop:~$ 

```

No errors.  Did it really load?

```

jessica@RedLaptop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          3018       2892        125          0       1878        366
-/+ buffers/cache:        647       2371
Swap:         7397          0       7397

```

Yes.

I think I'm good, for the moment.

---

### Post by Leppie on 2010-07-07
ok, i just now noticed you've got a wrong syntax in your fstab:
```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
**[COLOR=Red]/dev/sda5 UUID=ea097450-6c32-4f5d-89d2-ec238d21db48[/COLOR]**[COLOR=Black] /[/COLOR]              ext3    defaults,errors=remount-ro 0       1
[COLOR=Red]**/dev/sda6 UUID=542620bc-0f65-4d5c-b1d7-487f2e0cd325**[/COLOR] none            swap    sw              0       0

```you either use the /dev/sdXY format, or you use the UUID format. but you can't use both at the same time for the same device...
here is what your fstab should look like:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# this is the root on /dev/sda5
UUID=ea097450-6c32-4f5d-89d2-ec238d21db48 /               ext3    defaults,errors=remount-ro 0       1
# this is the swap on /dev/sda6
UUID=60668a67-6b9a-410a-97b9-46e7a03a5d03 none            swap    sw              0       0
# this is the windows partition on /dev/sda2
UUID=043C708A3C70790E /windows ntfs auto,ro,users 0 0
# this is the music partition on /dev/sda1
UUID=641d9ed7-8906-4739-b3ed-6098a51844e0 /home/jessica/Music ext3 user,rw,nosuid,nodev,exec,async 0 0
# cd-rom
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0


```Edit: after reading your last post, you more or less figured this out yourself as well.

---


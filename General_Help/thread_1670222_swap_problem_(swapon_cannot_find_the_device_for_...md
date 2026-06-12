---
title: "swap problem (swapon: cannot find the device for ...)"
date: 2011-01-18
forum: General Help
---

### Post by andres.ordonez on 2011-01-18
Hi, I recently added the system monitor applet to one of my panels and realised that the swap space is never used. I read the Swap FAQ in the community documentation but couldn't solve the problem.

andres@andres-laptop:~$ cat /proc/sys/vm/swappiness 
60

(some appications open)
andres@andres-laptop:~$ free
             total       used       free     shared    buffers     cached
Mem:       3018928    1234988    1783940          0      32364     387884
-/+ buffers/cache:     814740    2204188
Swap:            0          0          0

(many applications open)
andres@andres-laptop:~$ free
             total       used       free     shared    buffers     cached
Mem:       3018928    2994644      24284          0       7408     341180
-/+ buffers/cache:    2646056     372872
Swap:            0          0          0

andres@andres-laptop:~$ sudo fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc17b6006

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1275    10240000   27  Unknown
/dev/sda2   *        1275        8924    61439996    7  HPFS/NTFS
/dev/sda3            8925       30401   172514002+   5  Extended
/dev/sda5            8925        9653     5855661   82  Linux swap / Solaris
/dev/sda6            9654       30401   166658278+  83  Linux

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x4db9b9e8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      121602   976760536    7  HPFS/NTFS


andres@andres-laptop:~$ cat /etc/fstab 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=e154ab05-4256-43fe-ba99-47f94b7f32b7 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=b3790e73-7855-4797-862f-ad8b8a30dcfd none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
andres@andres-laptop:~$ sudo swapoff -a
andres@andres-laptop:~$ sudo /sbin/mkswap /dev/sda5
Setting up swapspace version 1, size = 5855656 KiB
no label, UUID=5372e6d3-3e16-4fdf-9902-4eb4fbe3b3d5
andres@andres-laptop:~$ sudo swapon -a
swapon: cannot find the device for UUID=b3790e73-7855-4797-862f-ad8b8a30dcfd

I guess the last line says sums up the problem.

Any help would be very appreciated.

---

### Post by dabl on 2011-01-18
Open a terminal, and paste in this command:

```
sudo blkid -c /dev/null -o list
```

and post back with the output.

---

### Post by andres.ordonez on 2011-01-18
andres@andres-laptop:~$ sudo blkid -c /dev/null -o list
[sudo] password for andres: 
device                                         fs_type         label            mount point                                        UUID
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------
/dev/sda1                                      vfat            PQSERVICE        (not mounted)                                      EAEE-EB49
/dev/sda2                                      ntfs            ACER             (not mounted)                                      3A240EDB240E99D1
/dev/sda5                                      swap                             (not mounted)                                      5372e6d3-3e16-4fdf-9902-4eb4fbe3b3d5
/dev/sda6                                      ext3                             /                                                  e154ab05-4256-43fe-ba99-47f94b7f32b7
/dev/sdc1                                      ntfs            TOSHIBA EXT      /media/TOSHIBA EXT                                 AEDC9232DC91F535

---

### Post by dabl on 2011-01-18
OK, as you can see, /etc/fstab has a UUID for swap, but the blkid output shows a different UUID.

Open your text editor with root privileges, open /etc/fstab, and carefully replace the UUID number with the correct one from the blkid output.  You can copy and paste from the terminal output, but be careful not to include the quote marks in the /etc/fstab line. Don't forget to do File > Save before you exit gedit.

Then issue ```
sudo mount -a
``` to mount it, and then you can check it with ```
sudo mount
```, and it should be mounted correctly.

---

### Post by andres.ordonez on 2011-01-18
well I don't really understand the output of mount so here it is:

andres@andres-laptop:~$ sudo mount -a
[1]+  Done                    sudo gedit /etc/fstab
andres@andres-laptop:~$ sudo mount
/dev/sda6 on / type ext3 (rw,relatime,errors=remount-ro,commit=0)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/andres/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=andres)
/dev/sdc1 on /media/TOSHIBA EXT type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)

is it ok now?

---

### Post by andres.ordonez on 2011-01-18
I don't think it's ok, the swap space is still 0% in use

---

### Post by hawkmage on 2011-01-18
Why are you concerned that Swap is not being used?  Are you running out of physical memory?

Like dabl asked what do you get when you run the command:
```
sudo blkid -c /dev/null -o list
```

---

### Post by andres.ordonez on 2011-01-18
Well I posted the output of "sudo blkid -c /dev/null -o list" before, but since I posted it twice by mistake I reported one of the posts for the moderator to delete it, but it seems like both were deleted, anyway here's the output:

andres@andres-laptop:~$ sudo blkid -c /dev/null -o list
device                                         fs_type         label            mount point                                        UUID
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------
/dev/sda1                                      vfat            PQSERVICE        (not mounted)                                      EAEE-EB49
/dev/sda2                                      ntfs            ACER             (not mounted)                                      3A240EDB240E99D1
/dev/sda5                                      swap                             (not mounted)                                      4d85d9bf-0085-45fd-96c3-986843bce895
/dev/sda6                                      ext3                             /                                                  e154ab05-4256-43fe-ba99-47f94b7f32b7
/dev/sdc1                                      ntfs            TOSHIBA EXT      /media/TOSHIBA EXT                                 AEDC9232DC91F535

andres@andres-laptop:~$ cat /etc/fstab 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=e154ab05-4256-43fe-ba99-47f94b7f32b7 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=4d85d9bf-0085-45fd-96c3-986843bce895 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

I don't think I'm running out of physical memory but I'd like to solve it anyway (I'm on vacation hehe)

---

### Post by dabl on 2011-01-18
Hmmm -- where did that second post go?

> **andres.ordonez said:**
> well I don't really understand the 
is it ok now?

Nope.


The UUID of the partition that you are using for swap, apparently /dev/sda5, must be the UUID that is used in the /etc/fstab file to mount it.

The /etc/fstab file that you listed looks right.

Try again in the terminal ```
sudo mount -a
```

and then post the output of ```
sudo mount
```

---

### Post by andres.ordonez on 2011-01-18
andres@andres-laptop:~$ sudo mount
/dev/sda6 on / type ext3 (rw,relatime,errors=remount-ro,commit=0)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/andres/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=andres)
/dev/sdc1 on /media/TOSHIBA EXT type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)

---

### Post by dabl on 2011-01-18
Hmmmmmm -- I'm confused!

Can you remove that Toshiba thingy, please?  Then, since the UUID of /dev/sda5 has changed twice already, let's have one more look at the output of ```
sudo blkid -c /dev/null -o list
```

(just to make sure it hasn't changed again)

---

### Post by andres.ordonez on 2011-01-18
andres@andres-laptop:~$ sudo blkid -c /dev/null -o list
[sudo] password for andres: 
device                                         fs_type         label            mount point                                        UUID
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------
/dev/sda1                                      vfat            PQSERVICE        (not mounted)                                      EAEE-EB49
/dev/sda2                                      ntfs            ACER             (not mounted)                                      3A240EDB240E99D1
/dev/sda5                                      swap                             (not mounted)                                      4d85d9bf-0085-45fd-96c3-986843bce895
/dev/sda6                                      ext3                             /                                                  e154ab05-4256-43fe-ba99-47f94b7f32b7

---

### Post by dabl on 2011-01-18
OK.   The UUID remains the same.  "not mounted" means ... it is not mounted.  So, something is not happening when you run the "sudo mount -a" command.  Do you get any error output in the terminal?

Here is the swap mount line from my /etc/fstab file.  Look at it carefully, and compare it to the mount line in your /etc/fstab file.  What is different (other than the UUID)?


```
UUID=8cee8dd4-94c1-4949-ae5e-5a7f065b0306       none            swap            sw                                            0    0
```

---

### Post by andres.ordonez on 2011-01-18
haha what I don't know is what means the output of mount, and no, I don't get any error.

---

### Post by dabl on 2011-01-18
I mean, when you open the terminal, and enter

```
sudo mount -a
```

does it give an error message?

---

### Post by andres.ordonez on 2011-01-18
No error

---

### Post by dabl on 2011-01-18
And ```
sudo swapon -a
``` still gives "no device"?

---

### Post by andres.ordonez on 2011-01-18
it gives no output, ah! but now it seems to be fine right?

andres@andres-laptop:~$ sudo blkid -c /dev/null -o list
device                                         fs_type         label            mount point                                        UUID
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------
/dev/sda1                                      vfat            PQSERVICE        (not mounted)                                      EAEE-EB49
/dev/sda2                                      ntfs            ACER             (not mounted)                                      3A240EDB240E99D1
/dev/sda5                                      swap                             <swap>                                             4d85d9bf-0085-45fd-96c3-986843bce895
/dev/sda6                                      ext3                             /                                                  e154ab05-4256-43fe-ba99-47f94b7f32b7

---

### Post by dabl on 2011-01-18
That looks right!  :popcorn:

---

### Post by andres.ordonez on 2011-01-18
> **dabl said:**
> Here is the swap mount line from my /etc/fstab file.  Look at it carefully, and compare it to the mount line in your /etc/fstab file.  What is different (other than the UUID)?


```
UUID=8cee8dd4-94c1-4949-ae5e-5a7f065b0306       none            swap            sw                                            0    0
```

Nothing is different (other than the UUID).

However the swap space is still "0% in use" even when I have Memory 90% in use by programs and 10% in use as cache. Should it be this way??

---

### Post by andres.ordonez on 2011-01-18
Well Mr. dabl I'm marking this thread as solved since the swap partition is now mounted thanks to you. I still have the question about the swap usage (previous post) though.

Thank you very much for your time.

---

### Post by Dvilef on 2011-01-18
i have a question I have a toshiba Satellite l355-s7902

250GB (5400 RPM) Serial ATA hard disk drive.


i trying to install 10.10 , i have a live cd, problem that i have is the installer is not reckonizing the harddrive,  

when i try to install it tells me that i have , 2.8 gb of space, that  must be the ram, i checked the hard drive , it is secure in place, i  tried to also install other versions , nothing, same thing with all,  installers can find harddrive, is thier anything i can do to fix this  problem , with live cd, not sure how to get 10.10 to find my hard drive,  i research a little, some thing about the kernel, needing something, or  i could flash bios , or may be it's the harddrive, in some of the other  live cd i have tried 8.10 i get a black screen with a list of commands ,  im not sure what command would work , can somebody help

i also went in to bios using the f2 key and change for achi to compatitlity, it didn't help 


my computer is at a black screen at this point, toshiba logo comes up, prees any key to boot disc, i also tried window's nothing , error message , can find harddrive
my desktop is 2 years old it reads the ram but not the harddrive


sorry to reply to this thread , not sure how to make my own

---

### Post by hawkmage on 2011-01-18
The kernel will determine how aggressive to be with swapping based on the swappiness it will try to reclaim idle memory.

If swappiness is 100 it is very aggressive and will try to swap a memory page almost as soon as it is marked as idle.  

If swappiness is 0 the kernel will wait until the system has allocated app physical memory  but a process is asking for more before it swaps out a  memory page.  

If during normal operation your system doesn't run out of physical memory there is really isn't a reason to swap.  If you have swapping set to be very aggressive and the kernel swaps out memory that you periodically use you will experience a performance hit.  For example you have your email client running and it checks your email account every 5 minutes.  A portion of the email clients memory will be swapped out with aggressive swapping and every time it has to check for new mail it will have to swap memory into physical memory before it can run.  This will cause the email client process block on disk IO.  

If you run many applications and you do run into conditions where you run low on physical memory then you may want to increase the value of swappiness.   Also if you do a lot of IO on the file system you may want to have a higher then default swappiness to free up memory for caching.  

The bottom line is that memory usage and swapping being good or bad is dependent on your systems resources and usage but the ideal situation is to have enough physical memory to never have to swap and ample for disk cache.

---

### Post by andres.ordonez on 2011-01-18
@Dvilef
To make you own thread go to [www.ubuntuforums.com](www.ubuntuforums.com), log in, choose a category (which in your case should be "installation & upgrades") and click on the "New Thread" button. 

Could it be that you have other OS (like windows) occupying most of your hard drive? If so, then you can find plenty of documentation about dual booting around, you just have to google "ubuntu windows dual boot"

If not I don't know. Anyway you should make a new thread.

---

### Post by andres.ordonez on 2011-01-18
Thanks for the explanation hawkmage, I guess most of the time I don't really need the swap space since normally I have less than 50% of memory usage (programs + cache).

---

### Post by dabl on 2011-01-18
> **andres.ordonez said:**
>  I still have the question about the swap usage (previous post) though.


swap will not be used unless it is _needed_.  ;)

---

### Post by afrodeity on 2011-02-19
getting some swap weirdness.

```


sudo blkid -c /dev/null -o list
device     fs_type label    mount point    UUID
-------------------------------------------------------------------------------
/dev/sda1  ext4    Earth    /              b324b840-d156-453f-af15-fa79814e0122
/dev/sdb1  ntfs    Gaia     /media/Gaia    41FC62D27FCF8755

```

```

sudo swapon -a
swapon: cannot find the device for UUID=bd84fcd5-cbec-4fa2-9fc6-4fc639ceabd7

```

Also no entry for vm.swappiness in my sysctl.conf file. System has been locking up, and getting disk not available or not ready messages on boot for the swap uuid

```

sudo fdisk -l

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x213e213e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       23995   192739806   83  Linux
/dev/sda2           23996       24321     2618595    5  Extended
/dev/sda5           23996       24321     2618563+  82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0009fdb2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       60801   488384001    7  HPFS/NTFS

```

UPDATE: I ended up having to reformat my swap partition. Gparted showed it wasn't formatted, so some other OS wrote all over it!!!. Still trying to figure out what is going on with my sysctl.conf file and the disappearing swappiness. Wish there was a way of hardwiring the swap and partition size, gives me the jitters just thinking about what happens when you delete a partition by accident.

---


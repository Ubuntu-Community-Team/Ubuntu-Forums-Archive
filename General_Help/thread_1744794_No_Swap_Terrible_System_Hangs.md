---
title: "No Swap? Terrible System Hangs?"
date: 2011-04-30
forum: General Help
---

### Post by MegaLoler on 2011-04-30
When I upgraded to Natty my swap disappeared.  When I go to System Monitor it says it is using 0 out of 0 percent of the swap.

Also when I upgraded to Natty I have been getting terrible system hangs.  I only have 433 MiB of RAM... but still it has never ever been THIS bad.  Just running the software center alone causes the clock to freeze, the disk activity to constantly go nuts, the cursor to only budge every 5 seconds... etc.

I was wondering if there is a connection between the two.  Also how can I fix it?  Thanks

---

### Post by TeoBigusGeekus on 2011-04-30
Do you use unity?

---

### Post by dabl on 2011-04-30
You're pretty thin on memory to be running Ubuntu 11.04.  Having said that, it might be possible to improve the performance a bit.  I'd like to see the output of these:

```
sudo blkid -c /dev/null -o list
```

```
sudo mount
```

```
df -h
```

---

### Post by MegaLoler on 2011-04-30
I am not using Unity.

The outputs:
```
sudo blkid -c /dev/null -o list
device     fs_type label    mount point    UUID
-------------------------------------------------------------------------------
/dev/sda1  ntfs             (not mounted)  5E7CF2FC7CF2CE31
/dev/sda2  ext3             (not mounted)  2341437f-42d3-49f0-a310-f7c52448633e
/dev/sda3  ext4             /              b9fb82ec-e643-4d9c-82e3-252c41cea53a
/dev/sda5  swap             (not mounted)  8435cd6b-a6ea-4f29-912e-c600e5a014c1
/dev/sda6  swap             (not mounted)  8fe8d7c5-7cd8-4b81-9309-84161d95eecd
/dev/sda7  ext3             (not mounted)  2854963d-21fb-446e-ac6e-10e40d4752f6
/dev/sda8  swap             (not mounted)  6215a975-a9b1-4c53-af00-4afa351cf4f4
/dev/sda9  ext4             (not mounted)  8375fb21-212c-482c-b683-7937450f8985
/dev/sda10 swap             (not mounted)  f48a32c8-6b02-4f00-910e-a92eb81252fe
```

```
sudo mount
/dev/sda3 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
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
gvfs-fuse-daemon on /home/megaloler/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=megaloler)

```

```
df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3             7.0G  5.3G  1.4G  79% /
none                  212M  564K  211M   1% /dev
none                  217M  200K  217M   1% /dev/shm
none                  217M  220K  217M   1% /var/run
none                  217M     0  217M   0% /var/lock

```

Thanks

---

### Post by dabl on 2011-04-30
You have 4 swap partitions, and none of them are mounted -- that's a little weird. You only need one swap on a computer, but it does need to be mounted. OK, let me see the output of 

```
cat /etc/fstab
```

Also, can you say which of the 4 swaps is the largest, so we can mount it?  Or, just run

```
sudo fdisk -lu
```

and that will show the sizes.

---

### Post by MegaLoler on 2011-04-30
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda12 during installation
UUID=b9fb82ec-e643-4d9c-82e3-252c41cea53a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda13 during installation
UUID=8435cd6b-a6ea-4f29-912e-c600e5a014c1 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

```And I am not really sure which one is the largest.  How can I check?
EDIT: /dev/sda6 is the largest.

---

### Post by dabl on 2011-04-30
It's odd that what appears to be a legitimate swap partition defined in /etc/fstab is not mounted a boot. That is probably why the system is thrashing when you try do something.

You could change the UUID on the swap line in /etc/fstab to match the UUID for sda6:

8fe8d7c5-7cd8-4b81-9309-84161d95eecd

You can use Alt-F2 "gksudo /etc/fstab" to open /etc/fstab for editing.  After you have saved it, do this in the terminal:

```
sudo mount -a
```

and let's see if there is any error output.

---

### Post by MegaLoler on 2011-04-30
There was no error.

However gksudo /etc/fstab didn't do anything so I tried sudo gedit /etc/fstab from the terminal.  Is that fine?

---

### Post by dabl on 2011-04-30
> **MegaLoler said:**
> 

gksudo /etc/fstab didn't do anything 

That's what I get for answering the phone while typing an instruction.  :o

The correct instruction is "Alt-F2 gksudo gedit /etc/fstab".  You should not use "sudo" to run a GUI package such as gedit.  In a terminal you could issue "gksudo gedit" and it would launch it correctly.

OK, now I'd like to see the output of ```
sudo mount
``` again, and also 

```
sudo blkid -c /dev/null -o list
```

---

### Post by MegaLoler on 2011-04-30
```
/dev/sda3 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
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
gvfs-fuse-daemon on /home/megaloler/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=megaloler)

```

---

### Post by dabl on 2011-04-30
Do the blkid one too, please (I added it via editing later).

---

### Post by MegaLoler on 2011-04-30
Oops, sorry about that.
```
device                        fs_type     label        mount point                       UUID
------------------------------------------------------------------------------------------------------------------------------
/dev/sda1                     ntfs                     (not mounted)                     5E7CF2FC7CF2CE31
/dev/sda2                     ext3                     (not mounted)                     2341437f-42d3-49f0-a310-f7c52448633e
/dev/sda3                     ext4                     /                                 b9fb82ec-e643-4d9c-82e3-252c41cea53a
/dev/sda5                     swap                     (not mounted)                     8435cd6b-a6ea-4f29-912e-c600e5a014c1
/dev/sda6                     swap                     (not mounted)                     8fe8d7c5-7cd8-4b81-9309-84161d95eecd
/dev/sda7                     ext3                     (not mounted)                     2854963d-21fb-446e-ac6e-10e40d4752f6
/dev/sda8                     swap                     (not mounted)                     6215a975-a9b1-4c53-af00-4afa351cf4f4
/dev/sda9                     ext4                     (not mounted)                     8375fb21-212c-482c-b683-7937450f8985
/dev/sda10                    swap                     (not mounted)                     f48a32c8-6b02-4f00-910e-a92eb81252fe

```

---

### Post by dabl on 2011-04-30
OK, so it did not mount the swap line in /etc/fstab.  That's strange.

In a terminal, do this:

```
sudo swapon -a
```

and post back with any errors.  If there are no errors, then again do 

```
sudo blkid -c /dev/null -o list
```

and let's see if swap is mounted.

---

### Post by MegaLoler on 2011-04-30
sudo swapon -a gave this error:
```
swapon: /dev/sda6: swapon failed: Invalid argument
```

---

### Post by dabl on 2011-04-30
Hmmmmmmmmm.

I'm beginning to wonder if there were added or deleted partitions on that hard drive recently -- do you know if that happened?  Can you run ```
sudo fdisk -l
``` and post the output please?

---

### Post by MegaLoler on 2011-04-30
```
Disk /dev/sda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x42b442b3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        5898    47375648+   7  HPFS/NTFS
/dev/sda2            5899        7112     9744660   83  Linux
/dev/sda3   *        7112        8035     7417856   83  Linux
/dev/sda4            8035       10012    15881733    f  W95 Ext'd (LBA)
/dev/sda5            8035        8084      386040   82  Linux swap / Solaris
/dev/sda6            8084        8184      811240   82  Linux swap / Solaris
/dev/sda7            8185        8488     2441816   83  Linux
/dev/sda8            8489        8510      176672   82  Linux swap / Solaris
/dev/sda9            9163        9969     6476800   83  Linux
/dev/sda10           9969       10012      345080   82  Linux swap / Solaris


```

Yes actually, I deleted some old partitions with old versions of Ubuntu on them about a week ago.  I also installed 10.10 a few days before that.  (Which was later upgraded to the 11.04 I have now)

---

### Post by dabl on 2011-04-30
There used to be a file in /boot/grub called "devicemap", but I see it is no longer in the newest versions.  Hmmmmmmmm. I am confident that the problem began when you deleted partitions, and the system is now a bit confused about where the different partitions are located.

Let's try the mkswap command.  In a terminal

```
sudo mkswap /dev/sda6
```

and post back if you get errors.  If there are no errors, then again

```
sudo swapon /dev/sda6
```

---

### Post by MegaLoler on 2011-04-30
Wow, it worked.  I checked the system monitor and it shows the swap in use. :D  Is this permanent or is there anything else I need to do?

---

### Post by dabl on 2011-04-30
Cool. Made that look easy, didn't we?  :popcorn:


OK, you'd better do this, and then you can reboot and see if it automatically mounts the swap partition:

```
sudo update-initramfs -u
```

---

### Post by MegaLoler on 2011-04-30
Okay I did that.  But I will wait until have to wait until tonight to reboot because my monitor won't come on for a few hours after the last time it was turned off for some reason... :-?

But thanks a lot! :D  Now I will observe and see if it helped the hangs.

---

### Post by dabl on 2011-04-30
If it turns out to mount swap correctly when you boot, it might help another person if you edit the title on your original post and add "SOLVED" in front of the title.

Thanks and good luck!

---

### Post by oneadvent on 2011-10-02
To revive, I was trying to follow your steps here but mine I get is this: 
```
oneadvent@oneadvent-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
oneadvent@oneadvent-desktop:~$ sudo fdisk -lu

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2          206848  1438529535   719161344    7  HPFS/NTFS
/dev/sda4      1438529536  1465145343    13307904    7  HPFS/NTFS

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00059495

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048   484206591   242102272   83  Linux
/dev/sdb2       484208638   488396799     2094081    5  Extended
/dev/sdb5       484208640   488396799     2094080   82  Linux swap / Solaris
oneadvent@oneadvent-desktop:~$ vi /etc/fstab
oneadvent@oneadvent-desktop:~$ sudo mount -a
oneadvent@oneadvent-desktop:~$ sudo mount
/dev/sdb1 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
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
none on /proc/fs/vmblock/mountPoint type vmblock (rw)
/dev/sda4 on /media/FACTORY_IMAGE type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda2 on /media/HP type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
gvfs-fuse-daemon on /home/oneadvent/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=oneadvent)
oneadvent@oneadvent-desktop:~$ sudo blkid -c /dev/null -o list
device                   fs_type    label       mount point                  UUID
-----------------------------------------------------------------------------------------------------------------
/dev/sda1                ntfs       SYSTEM      (not mounted)                3A2EAF412EAEF4D3
/dev/sda2                ntfs       HP          /media/HP                    E8B6ACEBB6ACBC06
/dev/sda4                ntfs       FACTORY_IMAGE /media/FACTORY_IMAGE       FCCA08FDCA08B644
/dev/sdb1                ext4                   /                            2d0e4aed-f315-40e4-9f7f-470598282ffa
/dev/sdb5                swap                   (not mounted)                46a1e91d-e8b5-47b6-bf23-04a31a0a90b6
oneadvent@oneadvent-desktop:~$ sudo swapon -a
swapon: /dev/sda5: stat failed: No such file or directory
oneadvent@oneadvent-desktop:~$ sudo mkswap /dev/sda5
/dev/sda5: No such file or directory

```

Can you give me some ideas here? Never had this problem before.

---

### Post by thioshp on 2012-05-26
> **dabl said:**
> That's what I get for answering the phone while typing an instruction.  :o

The correct instruction is "Alt-F2 gksudo gedit /etc/fstab".  You should not use "sudo" to run a GUI package such as gedit.  In a terminal you could issue "gksudo gedit" and it would launch it correctly.

OK, now I'd like to see the output of ```
sudo mount
``` again, and also 

```
sudo blkid -c /dev/null -o list
```
Thank you dabl for helping me solve this problem. I followed your steps and after restarting, my swap was back.

---

### Post by oldos2er on 2012-05-26
Old thread closed.

---


---
title: "Swap Lost:  Dual Booting Xubuntu Lucid &amp; Mint 9"
date: 2011-04-21
forum: General Help
---

### Post by fleamour on 2011-04-21
My swap partition is missing in action, please help!

```
cat /etc/fstab
```
Returns:

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=165ae8f3-1d73-4071-b0bd-0f6e9d25ea92 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda2 during installation
UUID=d744d552-9d76-46f9-851c-84f8875f2dba /home           ext4    defaults        0       2
# swap was on /dev/sda7 during installation
UUID=5c4bb4ce-55f5-4601-aa90-79650941f77f none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

```
sudo swapoff -a
sudo /sbin/mkswap /dev/sda7
sudo swapon -a
```
Returns:

swapon: cannot find the device for UUID=5c4bb4ce-55f5-4601-aa90-79650941f77f

G Parted fails to launch so that is not an option.


:(:confused::(

---

### Post by fleamour on 2011-04-21
OK, I'm confused, UUIDS seem to jump around every reboot:

```
sudo blkid
```
[sudo] password for user: 
/dev/sda1: UUID="165ae8f3-1d73-4071-b0bd-0f6e9d25ea92" TYPE="ext4" 
/dev/sda2: UUID="d744d552-9d76-46f9-851c-84f8875f2dba" TYPE="ext4" 
/dev/sda5: UUID="8f4ec729-6453-49bc-8954-46b0f54978ab" TYPE="ext4" 
/dev/sda6: UUID="49e31124-9446-41f3-973a-44dedcb8a9ff" TYPE="swap" 
/dev/sda7: UUID="025e1b5a-adcf-4723-bf05-52f0662d8eab" TYPE="swap" 
/dev/sdb1: LABEL="TDK" UUID="9975-B739" TYPE="vfat" 
user@computer:~$ sudo swapoff -a
user@computer:~$ sudo /sbin/mkswap /dev/sda6
Setting up swapspace version 1, size = 522076 KiB
no label, **(?>**UUID=87eed974-84ed-4ad3-8614-4d1651bcb706**<?)**
user@computer:~$ sudo swapon -a
swapon: cannot find the device for UUID=49e31124-9446-41f3-973a-44dedcb8a9ff

I set sda7 as swap but it should be ext4 I think.

---

### Post by ajgreeny on 2011-04-21
Firstly, you do not need to have two swap partitions, so it may be possible to change that for a start, though if they are both quite small, it may not be worth doing anything at this stage.

Secondly, can you show the output of ```
sudo fdisk -l
```from either of the two OSs. 

Third, UUIDs **do not** change at rebooting, they are fixed, and only change when partitions are formatted.

I suspect your problem is because you have set up two swap partitions when installing the two OSs, so it would be helpful to see the outputs of ```
cat /etc/fstab
free -m
``` from both xubuntu and mint, as it will show if you have a swap available in both systems, even if it is not the same swap in each of them.

---

### Post by coffeecat on 2011-04-21
When you ran the mkswap command in this sequence...

> **fleamour said:**
> 
```
sudo swapoff -a
sudo /sbin/mkswap /dev/sda7
sudo swapon -a
```

... you changed the UUID of sda7. As ajgreeny rightly says, UUIDs do not change spontaneously.

Apart from the three commands ajgreeny suggested:

```
sudo fdisk -lu
cat /etc/fstab
free -m
```Please run again...

```
sudo blkid
```... so we have the output of that to compare with your /etc/fstab

---

### Post by fleamour on 2011-04-22
I agree I messed up.  Neither OS can hibernate but there is only one swap partition shared between both.  Both OSs comprise of a root partition & a /home partition. Thanks for helping! 
```
sudo fdisk -l
```

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x3d9f3015

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1245     9999360   83  Linux
/dev/sda2            1245        6101    39005898+  83  Linux
/dev/sda3            6102       12161    48676919+   5  Extended
/dev/sda5            6102        7376    10241406   83  Linux
/dev/sda6           12097       12161      522081   82  Linux swap / Solaris
/dev/sda7            7377       12096    37913368+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 3997 MB, 3997171712 bytes
17 heads, 17 sectors/track, 27013 cylinders
Units = cylinders of 289 * 512 = 147968 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x16786eca

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              28       27014     3899456    b  W95 FAT32
```
sudo fdisk -lu
```

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders, total 195371568 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x3d9f3015

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    20000767     9999360   83  Linux
/dev/sda2        20000768    98012564    39005898+  83  Linux
/dev/sda3        98012626   195366464    48676919+   5  Extended
/dev/sda5        98012628   118495439    10241406   83  Linux
/dev/sda6       194322303   195366464      522081   82  Linux swap / Solaris
/dev/sda7       118495503   194322239    37913368+  83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 3997 MB, 3997171712 bytes
17 heads, 17 sectors/track, 27013 cylinders, total 7806976 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x16786eca

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            8064     7806975     3899456    b  W95 FAT32
```
cat /etc/fstab
```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=165ae8f3-1d73-4071-b0bd-0f6e9d25ea92 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda2 during installation
UUID=d744d552-9d76-46f9-851c-84f8875f2dba /home           ext4    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=49e31124-9446-41f3-973a-44dedcb8a9ff none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
fleamour@IBM-T21:~$ 
```
free -m
```
             total       used       free     shared    buffers     cached
Mem:           497        473         23          0         27        214
-/+ buffers/cache:        231        266
Swap:            0          0          0
```
sudo blkid
```

/dev/sda1: UUID="165ae8f3-1d73-4071-b0bd-0f6e9d25ea92" TYPE="ext4" 
/dev/sda2: UUID="d744d552-9d76-46f9-851c-84f8875f2dba" TYPE="ext4" 
/dev/sda5: UUID="8f4ec729-6453-49bc-8954-46b0f54978ab" TYPE="ext4" 
/dev/sda6: UUID="87eed974-84ed-4ad3-8614-4d1651bcb706" TYPE="swap" 
/dev/sda7: UUID="025e1b5a-adcf-4723-bf05-52f0662d8eab" TYPE="swap" 
/dev/sdb1: LABEL="TDK" UUID="9975-B739" TYPE="vfat"

---

### Post by coffeecat on 2011-04-22
First thing. When you are asked to post the output of terminal commands, please post these within code tags for legibility. Compare your fdisk -lu output:

=============================================
Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders, total 195371568 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x3d9f3015

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    20000767     9999360   83  Linux
/dev/sda2        20000768    98012564    39005898+  83  Linux
/dev/sda3        98012626   195366464    48676919+   5  Extended
/dev/sda5        98012628   118495439    10241406   83  Linux
/dev/sda6       194322303   195366464      522081   82  Linux swap / Solaris
/dev/sda7       118495503   194322239    37913368+  83  Linux
=============================================

to:

```
Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders, total 195371568 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x3d9f3015

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    20000767     9999360   83  Linux
/dev/sda2        20000768    98012564    39005898+  83  Linux
/dev/sda3        98012626   195366464    48676919+   5  Extended
/dev/sda5        98012628   118495439    10241406   83  Linux
/dev/sda6       194322303   195366464      522081   82  Linux swap / Solaris
/dev/sda7       118495503   194322239    37913368+  83  Linux
```Second. There's something not right with /dev/sda7. In the fdisk output it appears as an ext3/ext4 formatted partition - code 83 - and is approx 38.8GB in size. But from blkid:

```
/dev/sda7: UUID="025e1b5a-adcf-4723-bf05-52f0662d8eab" TYPE="swap"
```I think this is because you ran the mkswap command on an ext3/4 partition, but the mkswap command didn't amend the partition table entry - hence the output from fdisk. I suggest you reformat this partition using Gparted to make sure the partition table corresponds with the filesystem in the partition. I'm sure you don't need a swap partition of 38.8GB. :)

Partition /dev/sda6 is about 535MB, which is more like it. Edit /etc/fstab with this command:

```
gksudo gedit /etc/fstab
```

**EDIT**: Oops, you're using Xubuntu. Use whatever graphical text editor comes in place of gedit in Xubuntu. (end edit).

Change these lines:

```
# swap was on /dev/sda6 during installation
UUID=49e31124-9446-41f3-973a-44dedcb8a9ff none            swap    sw              0       0
```... to ...

```
# swap was on /dev/sda6 during installation
UUID=87eed974-84ed-4ad3-8614-4d1651bcb706 none            swap    sw              0       0
```Then you should be OK.

---

### Post by fleamour on 2011-04-22
OK, thanks!  That makes sense.  Mousepad is the txt editor of choice!  Either that or sudo nano.

Can I make sda7 ext4 again?  I am pretty sure it's the /home partition of Mint, but I messed up trying to make it swap.

---

### Post by coffeecat on 2011-04-22
> **fleamour said:**
> Can I make sda7 ext4 again?  I am pretty sure it's the /home partition of Mint, but I messed up trying to make it swap.

If you simply want to reformat it and not bother with any data that might have been on it, use Gparted which will ensure the partition table is correct. If it was the Mint home partition and there is data you want to recover then you'll need to use testdisk to see if you can recover the partition itself or photorec (which comes with testdisk) for individual files.

---

### Post by fleamour on 2011-04-22
After formatting as ext4, can I set it to be seen & used as Mint's /home partition?  Or maybe I should just reinstall Mint?

GParted will not launch but hopefully after setting swap it might.

---

### Post by coffeecat on 2011-04-22
If you reformat it you will lose all your Mint /home settings so you will need to re-install Mint. Which is why I mentioned testdisk. But you could well have lost them anyway after converting the partition to a swap partition.

Gparted's failure to launch would have nothing to do with swap not being mounted. If Gparted in your HD install is playing up, you could always use the live CD.

---

### Post by fleamour on 2011-04-22
Mint is box fresh so will probs just reinstall, though fixing Xubuntu's fstab to look for correct swap partition will help.

I tried GParted live CD also Parted Magic, they both crashed when detecting partitions, probs 'cus I borked sda7?  Haha, ah well, reinstall it is...

---

### Post by fleamour on 2011-04-22
I have changed the UUID in /fstab as per advice, but am getting this error:

```
user@laptop:~$ sudo swapoff -a
[sudo] password for user: 
user@laptop:~$ sudo /sbin/mkswap /dev/sda6
Setting up swapspace version 1, size = 522076 KiB
no label, UUID=8e2376a2-13b2-44f7-9485-e1d8c94f4783
user@laptop:~$ sudo swapon -a
swapon: cannot find the device for UUID=87eed974-84ed-4ad3-8614-4d1651bcb706
```

Am I being thick?

---

### Post by coffeecat on 2011-04-22
You've done it again!

> **fleamour said:**
> ```
user@laptop:~$ sudo /sbin/mkswap /dev/sda6
```

Why??!!

Read my post #4

---

### Post by fleamour on 2011-04-22
Ahhhh...

My code ignorance, so running that command changes the UUID.  I had wondered why that was the case.  If I merely correct /fstab from blkid output, hibernation will be restored?

I thought I was merely turning swap off, reassigning partition, turning on again.  The fact it changes UUID is baaaaaddd.  Shame on me, keep up at the back there lad!


[-X:?:[-X

---

### Post by coffeecat on 2011-04-22
You have a choice. Either run blkid to get the new UUID and edit fstab once again.

Or - run mkswap, but this time with the -U option to assign the UUID of your choice. Read 'man mkswap' if you need more. :)

---

### Post by fleamour on 2011-04-22
Done!  Now for a reboot me thinks.  I can "blkid" & "sudo mousepad /etc/fstab" blindfold now!

Cue annoying smiley:

):P:p):P

(Hello)

Thou art :KS

---

### Post by fleamour on 2011-04-22
Hibernation will make all the right noises shutting down, but upon rebooting it'll start at Grub menu again insteada coming outa hibernation.

I'm thinking maybe 'cus sda7 (borked) swap is still on the scene.  Time for a reformat.

---

### Post by fleamour on 2011-04-23
Bit worried now.  Have restored from Clonezilla image ***but*** GParted still crashes & Mint's partitioner will hang still, after choosing keyboard layout.

Any idea why?  I restored from backup thinking it would cure this behaviour.  I've found in Windows world, zeroing every sector then restoring can cure this kinda problem.  Is there a linux alternative?  I can always load Kill Disk from floppy.

Help!?!

---

### Post by fleamour on 2011-04-23
OK!  'twas my USB key, removed & now GParted works.  Phew!  Simple solution...

---


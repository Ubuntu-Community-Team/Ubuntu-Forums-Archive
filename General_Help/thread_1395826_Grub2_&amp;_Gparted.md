---
title: "Grub2 &amp; Gparted"
date: 2010-02-01
forum: General Help
---

### Post by bernardomh on 2010-02-01
Hi everyone i'm new to Ubuntu, i installed Karmic about 2 weeks ago and i'm still getting used to it. I'm using an Acer Aspire One with dual boot, i have Karmic and Windows XP.
When i first installed ubuntu grub2 started with no problems but now it doesn't boot automatically, i have to press enter to select which OS i want to use. I already veryfied that the time is not set to "-1", right now it is "2" but it doesn't boot automatically, can somebody tell what to do or if i need to reinstall grub2, how?

Another issue is i want to take a part of windows partition and paste it into ubuntu. I mean, when i first installed ubuntu the partitions were 50gb for ubuntu 50gb for windows, i have about 30gb free on the windows partition and want to paste them on the ubuntu partition so that i have 80 gb ubuntu  20 gb windows, i already ran the defragmentation procees in windows but still don't know how to go through the whole process.

I will be happy to provide any further information needed to solve this issues.
Thanks in advance.

---

### Post by muteXe on 2010-02-01
Hiya,
Can't help with grub2 I'm afraid, as i'm running 8.04. You'll have to shrink your xp partition , and grow your ubuntu using gparted (i think you can grow your ubuntu partition, i'll have to go check that).  

HOWEVER, when you come to resize your ubuntu parition you'll have to do it from the live CD, as you can't resize mounted partitions (and your ubuntu OS will be mounted if you dont do it from the live CD).

---

### Post by audiomick on 2010-02-01
You shouldn't have to re-install Grub2, I think.
Read through this
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
for info on configuring Grub2. It sounds like something is just messed up a bit.

As far as the partitioning goes, yes you should do it from the live CD, or the gparted live CD
[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

There is partitioning info here
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

Before you do anything with your partitions, backup any critical stuff. Clean up your windows install, remove anything that is not needed. De-frag again, maybe twice. Start windows a couple of times to make sure it is happy and allow it to do any disc checking it wants to do.

---

### Post by muteXe on 2010-02-01
Just found this on the (somewhat old) archive forum about *expanding* your ubuntu partition. It might apply to you:

> 
Unfortunately if your harddrive has the windows partition before the linux partition, you will not be able to grow it. The reason is because you can only expand the end of ext3 partitions with gparted, so if you want to expand it, I suggest using an external/extra harddrive to copy the ext3 partition, then delete it on the main harddrive and recopy it in the new, bigger location.

(source = [http://ubuntuforums.org/archive/index.php/t-244233.html](http://ubuntuforums.org/archive/index.php/t-244233.html))

Hopefully someone out there can confirm this for you?

---

### Post by michy99 on 2010-02-01
That is not true at all. You can grow the partition at either end or both ends. Assuming there is free space to do so, of course. When you add spce at the beginning, gparted actually moves the partition to the new beginning and adds whatever is necessary at the end.

---

### Post by drs305 on 2010-02-01
bernardomh,

Welcome to Ubuntu and the Ubuntu forums.  :-)

Here is a link on how to expand your / partition:
[http://ubuntuforums.org/showthread.php?t=1219270]("http://ubuntuforums.org/showthread.php?t=1219270")

As for the Grub 2 issue, please post the results of meierfra's [boot info script]("http://bootinfoscript.sourceforge.net/"). Please post the results with "code tags". (Use the # option in the post menu).

---

### Post by jimbob on 2010-02-01
Note that anytime you change anything about a partition, ie grow, shrink, etc, the system will generate a new UUID for it.  This means that after you are all done you will have to run update-grub so that your bootups will work again.

---

### Post by bernardomh on 2010-02-01
I want to thank everyone for the support and information, it's making it easier to move to Ubuntu. =D

I successfully took some space from the windows xp partition, i ran the defragmentation application and used Norton's Partition Magic, i could leave 20GB free space and tried to add this ones to my Ubuntu partition using gparted in a flashdrive but i couldn't do it (i hadn't checked all the links you posted here =P ). So now i have my main Ubuntu partition and a 20GB extra partition, maybe it is also good to have it like that, that partition is supposedly mounted but i cannot see anywhere it doesn't show on the places menu or on the desktop if you can give me some more advice i'd be more than thankful.

As for the grub2 issue, i just went to synaptic package manager and selected all the instances for grub and reinstalled them, now it works fine.

Thank you aaaaaallllll!!!!!!!

---

### Post by audiomick on 2010-02-02
> **bernardomh said:**
>  So now i have my main Ubuntu partition and a 20GB extra partition, maybe it is also good to have it like that, that partition is supposedly mounted but i cannot see anywhere...

Even if it is not showing up anywhere else, it should be visible under "places" in "Computer".

Is it there?

Edit:
Post #3 in this
[http://ubuntuforums.org/showthread.php?t=1395889](http://ubuntuforums.org/showthread.php?t=1395889)
might be relevant as well.

---

### Post by bernardomh on 2010-02-03
It is not on Places -> Computer
I have:
120 GB Harddisk
Filesystem
That's all! =S
I used the commands to set the mount point for the 20gb partition and labeled it Ondskapt but its not there

---

### Post by drs305 on 2010-02-03
Please provide the results of the following commands:
```

sudo blkid -c /dev/null
sudo fdisk -l
cat /etc/fstab
mount

```

Place the results between "code" tags, which you can call up by pressing the # symbol in the post's menu.

---

### Post by bernardomh on 2010-02-03
```
sudo blkid -c /dev/null
/dev/sda1: LABEL="PQSERVICE" UUID="0159-6699" TYPE="vfat" 
/dev/sda2: UUID="A4A48D83A48D58A6" LABEL="ACER" TYPE="ntfs" 
/dev/sda4: LABEL="Ondskapt" UUID="28ccce8f-b3fa-44ff-90e7-3a092f182117" TYPE="ext4" 
/dev/sda5: UUID="77133c9b-54d1-49b8-a305-a49797a032fb" TYPE="ext4" 
/dev/sda6: UUID="d571c3a0-4a85-4955-ad19-6c67d9755851" TYPE="swap" 
/dev/mmcblk0p1: SEC_TYPE="msdos" UUID="423D-2191" TYPE="vfat" 
/dev/mmcblk1p1: SEC_TYPE="msdos" LABEL="PROYECTO" UUID="6445-F456" TYPE="vfat" 

---------------------------------------------

sudo fdisk -l
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x11a8ba38

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         637     5116671   12  Compaq diagnostics
/dev/sda2   *         638        5517    39198600    7  HPFS/NTFS
/dev/sda3            8068       14593    52420095    f  W95 Ext'd (LBA)
/dev/sda4            5518        8067    20482875   83  Linux
/dev/sda5            8068       14321    50235223+  83  Linux
/dev/sda6           14322       14593     2184808+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/mmcblk0: 125 MB, 125960192 bytes
8 heads, 32 sectors/track, 961 cylinders
Units = cylinders of 256 * 512 = 131072 bytes
Disk identifier: 0x00000000

        Device Boot      Start         End      Blocks   Id  System
/dev/mmcblk0p1               1         961      122959+   6  FAT16

Disk /dev/mmcblk1: 64 MB, 64225280 bytes
4 heads, 32 sectors/track, 980 cylinders
Units = cylinders of 128 * 512 = 65536 bytes
Disk identifier: 0xd084bdc6

        Device Boot      Start         End      Blocks   Id  System
/dev/mmcblk1p1               1         980       62656    6  FAT16
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(1, 0, 1) logical=(0, 1, 1)
Partition 1 has different physical/logical endings:
     phys=(979, 3, 32) logical=(979, 0, 32)

------------------------------------------

cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=77133c9b-54d1-49b8-a305-a49797a032fb /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=d571c3a0-4a85-4955-ad19-6c67d9755851 none            swap    sw              0       0
UUID=28ccce8f-b3fa-44ff-90e7-3a092f182117 /ondskapt ext4 defaults 0 0


-----------------------------------------

mount
/dev/sda5 on / type ext4 (rw,errors=remount-ro)
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
/dev/sda4 on /ondskapt type ext4 (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/uhu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=uhu)
/dev/mmcblk0p1 on /media/423D-2191 type vfat (rw,nosuid,nodev,uhelper=devkit,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)
/dev/mmcblk1p1 on /media/PROYECTO type vfat (rw,nosuid,nodev,uhelper=devkit,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)#

---------------
```

There it is! Proyecto is a SD card and the disk partition i can't find is the one named Ondskapt.
I really appreaciate your help!

---

### Post by drs305 on 2010-02-03
> **bernardomh said:**
> 
There it is! Proyecto is a SD card and the disk partition i can't find is the one named Ondskapt.
I really appreaciate your help!

It appears "Ondskapt" *is* mounted at /Ondskapt. You won't see it automatically on your Desktop because those must be mounted in /media. If you click on "Filesystem" in Nautilus you should see it listed as "Ondskapt". You could drag it to the lower left pane to create a shortcut.

You could alternatively change your fstab mount point entry for this partition to /media/Ondskapt after running this command (substitue your username):
```
sudo mkdir /media/Ondskapt && sudo chown -R *yourusername*: /media/Ondskapt
```

After making the change in fstab and saving the file, unmount then remount the partitions listed in fstab with:
```
sudo umount /dev/sda4 && sudo mount -a
```
It should then be mounted on /media/Ondskapt and also show on your Desktop and in Places.

---

### Post by bernardomh on 2010-02-03
Ok, i ran those commands and Ondskapt is now in media but not in places or in the desktop =S
Any other ideas?

---

### Post by drs305 on 2010-02-03
> **bernardomh said:**
> Ok, i ran those commands and Ondskapt is now in media but not in places or in the desktop =S
Any other ideas?

Can you see the **contents** of the partition?

Can you see other partitions in Places? Note, you should be able to create a shortcut in the lower half of the left panel (Side Pane) by dragging the folder there. That's not the end result we are looking for.

Can you see other partitions on the Desktop? If not, you can run this command:
```
gconftool-2 -t bool --set /apps/nautilus/desktop/volumes_visible true

```

---

### Post by bernardomh on 2010-02-03
Well in the desktop i have the icons for the SD card that is always plugged in my netbook and an external hard drive that i'm using right now.
After running that command it's the same.
What i'm asking is impossible to do? Or do i have to create the shortcut manually?
Because i think that by having the Ondskapt partition it should appear in places and in the desktop, but maybe i'm wrong. =S

---

### Post by bernardomh on 2010-02-04
Grub 2 has stopped working correctly (again) it just stops at the OS select screen. Any ideas? =S

---


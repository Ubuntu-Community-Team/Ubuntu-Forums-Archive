---
title: "USB not recognized on 10.10"
date: 2011-03-05
forum: General Help
---

### Post by Usbtroubles on 2011-03-05
Hi,
I have been trying to make my USB flash drive mount for a while now going through most of the forums i could find. I've got it working to the point that if i restart with the flash drive in the USB port it will recognize it upon startup, but if i remove it and try to put it back in....nothing. 

I have the cheap Acer Aspire One, 1 GB ram etc. 

I am very new to Linux but am loving Ubuntu except for this one problem! 

even if i go into disk utility and try to mount it it wont work, and i get this error message,

Error mounting: mount exited with exit code 1: helper failed with:
mount: according to mtab, /dev/sda1 is already mounted on /
mount failed

which from the little research i have done my computer wants to mount my sdb1 onto sda1 which is my hard drive. 

i've tried the usb stick in all the ports, nothing changes. it works fine in my windows xp computer. my camera is accepted as well as my mp3 player (although this has just recently started to work....magically really) 

if anyone can help me out i'd greatly appreciate it.

---

### Post by Hedgehog1 on 2011-03-06
> Error mounting: mount exited with exit code 1: helper failed with:
mount: according to mtab, **_/dev/sda1 is already mounted on /_**
mount failed

Based on this error, I think a look at your fstab file is in order.

Would you open /etc/fstab with text editor, and copy the text into your next post.

Also, do the same with the /etc/mtab text file.  Thanks!

***The Hedge***

:KS

---

### Post by Usbtroubles on 2011-03-06
Thanks for the quick reply!

here is what** fstab **in text editor had:

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sdb1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=c64cd77b-bcc7-4543-9ef0-5601aff4967a none            swap    sw              0       0



and here is what **mtab** had:

/dev/sda1 / ext4 rw,errors=remount-ro,commit=600 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
none /sys sysfs rw,noexec,nosuid,nodev 0 0
fusectl /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
none /dev devtmpfs rw,mode=0755 0 0
none /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
none /dev/shm tmpfs rw,nosuid,nodev 0 0
none /var/run tmpfs rw,nosuid,mode=0755 0 0
none /var/lock tmpfs rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/marc/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=marc 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0




also im pretty new to the whole terminal thing. so all of this means nothing to me haha
thanks again for your help!

---

### Post by Hedgehog1 on 2011-03-06
```

# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
**[COLOR="Red"]/dev/sdb1[/COLOR]**       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=c64cd77b-bcc7-4543-9ef0-5601aff4967a none            swap    sw              0       0

```

Your fstab file is a little, well, odd.

Normally we would see references to partitions using UUIDs when it is created by the install.  Your fstab is indeed asking to mount the sdb1 as the '/'.

It looks like you have done some *creative* things on your system.

I suggest doing this:

```
gksudo gedit /etc/fstab
```

comment out one line (in red) and add the new one (in green)

```
proc            /proc           proc    nodev,noexec,nosuid 0       0
[COLOR="Red"]**#**/dev/sdb1       /               ext4    errors=remount-ro 0       1[/COLOR]
[COLOR="YellowGreen"]/dev/sda1       /               ext4    errors=remount-ro 0       1[/COLOR]
```

after a reboot, you *should* be able to plug your USB drive in after booting and have it show up.

***The Hedge***

:KS

p.s.  Did you know your swap space ***may*** also looking for sdb5?:

```
# swap was on **[COLOR="RoyalBlue"]/dev/sdb5[/COLOR]** during installation
UUID=c64cd77b-bcc7-4543-9ef0-5601aff4967a none            swap    sw              0       0
```

---

### Post by Usbtroubles on 2011-03-08
well hedgehog...you did it! 

thanks a ton i really appreciate you fixing this. and i have no idea what i did, i had problems with this since i installed ubuntu (less than 2 weeks ago)

the only thing now is that it wont let me unmount or eject it......

i can do it if i use disk utility and unmount and then safe removal, but i was wondering if you had a quick fix for this. 
should i post a new thread for this question? im new to forums too.....


i get this if i try to unmount the desktop icon

                     umount: /media/usb0 is not in the fstab (and you are not root)

this if i try to eject/safely remove drive the USB icon from 'computer' 

                     One or more partitions are busy on /dev/sdb

thanks again

---


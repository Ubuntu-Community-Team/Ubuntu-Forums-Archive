---
title: "Second Hard Drive Not Mounting At Boot"
date: 2011-06-01
forum: General Help
---

### Post by Chriske on 2011-06-01
Hi,

I just installed a second hard drive in my desktop. It shows in the BIOS.

I followed the procedure here *[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)* to install it in Ubuntu, except I formatted the drive to ext4 not ext3.

It mounts automatically without problem once I am in Ubuntu and I can read/write to it.

My issue is that it won't mount at boot. I get past GRUB and a few seconds later receive an error message giving me an option 'S' to skip, or 'M' to manually mount.

What I noticed is that the logical name for the drive (used *sudo lshw -C disk* to display) seems to change at each boot.

It goes from */dev/sdb* to */dev/sdf* and vice versa.

So, I'm thinking this is the problem since I can only add it to */etc/fstab* according to what I last saw.

Any ideas please?

---

### Post by matt_symes on 2011-06-01
Hi

It's best to use UUID's to mount the drive in fstab and not device names because, as you have seen, they can change unless you set up a udev rule for the drive. With the drive plugged in....

Open a terminal and type

```
cat /etc/fstab
```

Then type 

```
sudo blkid -c /dev/null
```

Enter your password. It will not be echoed to the screen. This is normal.

Post the results of both commands back here by copying and pasting from the terminal window.

Kind regards

---

### Post by Locke_99GS on 2011-06-01
If the device name changes (which is peculiar, BTW) you can direct fstab to the drive's UUID. Use blkid to get the drive's UUID, and use that instead of the device name in fstab.
```
blkid
```


As an *example*, this is my root entry in fstab - your UUID will be different:
```

UUID=c1a7f7b6-c1f0-4031-972d-15703259bb60 / ext4 errors=remount-ro,user_xattr,noatime 0 1

```

On my machine, the drive UUID=c1a7f7b6-c1f0-4031-972d-15703259bb60 is sda5. If this partition were to somehow become sda6 or sdb2, it would still be detected and mount properly, as the UUID is not implicit of physical device location or order.

---

### Post by Chriske on 2011-06-01
Many thanks guys.

Here are the results of the commands matt-symes suggested:

cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=49f4684c-ccfa-4bfa-a4b3-1137077c647c /               ext4    errors=remount-ro 0       1
/dev/sda6 none swap sw 0 0

/dev/sdb1    /media/secondarydrive   ext4    defaults     0        2



sudo blkid -c /dev/null

/dev/sda1: LABEL="RECOVERY" UUID="6284C84A84C82281" TYPE="ntfs" 
/dev/sda5: UUID="49f4684c-ccfa-4bfa-a4b3-1137077c647c" TYPE="ext4" 
/dev/sda6: UUID="cb3f31fb-be56-4668-80d0-6e01ffffe246" TYPE="swap" 
/dev/sdf1: UUID="08ce0e85-b1df-4fa2-a35f-617162d616d7" TYPE="ext4"

"If the device name changes (which is peculiar, BTW)" - it seemed so to me too. I'd like to get to the bottom of why this happens.

---

### Post by Locke_99GS on 2011-06-01
Try this, if it appears to be what you're looking for.

```
UUID=08ce0e85-b1df-4fa2-a35f-617162d616d7 /media/secondarydrive ext4 defaults 0 2
```

edit: instead of the sdb1 entry. Comment or remove the current sdb1 entry.

---

### Post by matt_symes on 2011-06-01
Hi

> **Chriske said:**
> Many thanks guys.

Here are the results of the commands matt-symes suggested:

cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=49f4684c-ccfa-4bfa-a4b3-1137077c647c /               ext4    errors=remount-ro 0       1
/dev/sda6 none swap sw 0 0

/dev/sdb1    /media/secondarydrive   ext4    defaults     0        2



sudo blkid -c /dev/null

/dev/sda1: LABEL="RECOVERY" UUID="6284C84A84C82281" TYPE="ntfs" 
/dev/sda5: UUID="49f4684c-ccfa-4bfa-a4b3-1137077c647c" TYPE="ext4" 
/dev/sda6: UUID="cb3f31fb-be56-4668-80d0-6e01ffffe246" TYPE="swap" 
/dev/sdf1: UUID="08ce0e85-b1df-4fa2-a35f-617162d616d7" TYPE="ext4"

"If the device name changes (which is peculiar, BTW)" - it seemed so to me too. I'd like to get to the bottom of why this happens.

Change your fstab from
```

cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc nodev,noexec,nosuid 0 0
# / was on /dev/sda5 during installation
UUID=49f4684c-ccfa-4bfa-a4b3-1137077c647c / ext4 errors=remount-ro 0 1
/dev/sda6 none swap sw 0 0

/dev/sdb1 /media/secondarydrive ext4 defaults 0 2
```

to
```

cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc nodev,noexec,nosuid 0 0
# / was on /dev/sda5 during installation
UUID=49f4684c-ccfa-4bfa-a4b3-1137077c647c / ext4 errors=remount-ro 0 1
/dev/sda6 none swap sw 0 0

**UUID=08ce0e85-b1df-4fa2-a35f-617162d616d7 /media/secondarydrive ext4 defaults 0 2**
```

Make sure the drive is not mounted. Check the drive is mounting correctly by typing

```
sudo mount -a
```

If that gives no error the reboot your PC to check. If it does give error then post back any errors.

Kind regards

---

### Post by Chriske on 2011-06-01
That worked a treat, thanks! :D

I rebooted a couple of times without problem.

Many thanks again for the help, both. Much appreciated indeed.

BTW, I found another thread with the same problem ([http://ubuntuforums.org/showthread.php?t=1707996](http://ubuntuforums.org/showthread.php?t=1707996)). A poster there said this about this logical name runaround:
[INDENT] "There is just no guarantee which order the drives will get detected and that often determines how they get labelled"
[/INDENT]

---


---
title: "Help with mounting second HD"
date: 2011-11-20
forum: General Help
---

### Post by strange_cathect on 2011-11-20
Hi, I have a drive that I'm trying to mount properly in my fstab file. It isn't showing up in my computer properly. Can someone look over my fstab and give me a hand?
> 
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sdb2 during installation
UUID=16e618e9-50dc-45d8-961c-2c83ab86c289 /               ext4    errors=remount-ro 0       1
# /Backup was on /dev/sda1 during installation
UUID=ab8f0ed1-1f0d-4276-b47e-4946bd6412e9 /Backup         ext4    defaults        0       2
# swap was on /dev/sdb1 during installation
UUID=b7a22ef0-397e-4c86-8a70-0784a06dc536 none            swap    sw              0       0

I am trying to mount my /dev/sda drive as /Backup. But it isn't working right now correctly.

---

### Post by quadproc on 2011-11-20
> **strange_cathect said:**
> Hi, I have a drive that I'm trying to mount properly in my fstab file. It isn't showing up in my computer properly
At a casual glance, your fstab appears to be OK.  Can  you give us more details?

It would be helpful to know what symptoms you see, and when you see them.  Does the system boot successfully?  Have you very carefully checked the UUID to be sure that it is completely correct?  Is the /etc/fstab file correctly named and with correct permissions?  Which editor did you use to make your fstab changes?  Did you use sudo when making or copying or moving the fstab file?

quadproc

---

### Post by San_SS! on 2011-11-20
For what I see I would bet that the cause of your problems is one of:

 * /Backup does not exist. Remember that mountpoint's folder must exist.
 * The UUID of your partition has changed. Have you formatted it recently?

Hope this helps!

---

### Post by strange_cathect on 2011-11-20
Hi,

Thanks for your help. It is not mounting as a "device." Instead, the folder "Backup" appears in the file system.

How can I do that?

---

### Post by San_SS! on 2011-11-20
Have you checked if the UUID is correct? Do that by doing:
```
$ ls -la /dev/disk/by-uuid/
```

---

### Post by strange_cathect on 2011-11-20
> drwxr-xr-x 2 root root 120 2011-11-20 20:11 .
drwxr-xr-x 6 root root 120 2011-11-20 18:56 ..
lrwxrwxrwx 1 root root  10 2011-11-20 18:56 16e618e9-50dc-45d8-961c-2c83ab86c289 -> ../../sdb2
lrwxrwxrwx 1 root root   9 2011-11-20 20:11 9CFF-5463 -> ../../sdd
lrwxrwxrwx 1 root root  10 2011-11-20 18:56 ab8f0ed1-1f0d-4276-b47e-4946bd6412e9 -> ../../sda1
lrwxrwxrwx 1 root root  10 2011-11-20 18:56 b7a22ef0-397e-4c86-8a70-0784a06dc536 -> ../../sdb1


I also attached a screenshot. I used to have the drive appear as a "device" like the sansa clip you seen in the picture. Instead, I have a folder called /Backup within my file system, as you can see. I want to automount this partition (sda1) automatically when I log in.

Does it need to be /media/Backup or something?

---

### Post by San_SS! on 2011-11-20
But then, it is mounted. If you mount it using the fstab(or mount command) you won't be seeing it as a "device". Just access it through the Backup folder. I don't know how to make it to appear as a device, or even if it is possible.

---


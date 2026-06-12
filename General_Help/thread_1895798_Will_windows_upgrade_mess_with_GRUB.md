---
title: "Will windows upgrade mess with GRUB?"
date: 2011-12-15
forum: General Help
---

### Post by DuxWonder on 2011-12-15
Hello Forum,

I have a dual hard drive setup, with Windows 7 on the Main and Ubuntu 12.04 alpha on the second. I've been looking into trying the Windows 8 developer preview, but am currently unaware if that might interfere with GRUB, as it's installed on the Windows 7 hard drive. Does anyone have advice/ previous experience?

-DuxWonder

---

### Post by seawolf167 on 2011-12-15
Any fresh install of Windows is basically guaranteed to overwrite your MBR. You can easily re-write it back to Grub following [this guide ]("https://help.ubuntu.com/community/Grub2#Reinstalling_GRUB2")though.

As usual, backups are always a good idea - I suggest [Clonezilla ]("http://www.clonezilla.org")to make full disk images in case something goes wrong.

---

### Post by DuxWonder on 2011-12-15
Thanks for the guide! I'll cross my fingers and see what happens...

---

### Post by N00b-un-2 on 2011-12-15
reinstalling grub is very easy, and to reiterate, yes.  Installing windows, restoring windows, running Windows startup repair, etc.  will almost always overwrite your mbr.

to get your GRUB menu back after messing around with Windows, follow these steps:

1) boot up a live CD

2) open a terminal

3) Find out which partition you have Ubuntu installed on (usually /dev/sdaX)
```
sudo fdisk -l
```

4) mount your Ubuntu install and bind /proc, /bin and /dev
```
sudo mount /dev/sdaX /mnt # replace sdaX with the partition you have Ubuntu installed on
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo mount --bind /bin /mnt/bin

```

5) chroot into your Ubuntu install
```
sudo chroot /mnt
```

you are now effectively logged in as root on your Ubuntu install.

6) reinstall grub
```
sudo apt-get install grub # It should already be installed, but just in case...
sudo grub-install /dev/sda
sudo update-grub
```

Unmount your disks and reboot.  Bam!  Working grub

---

### Post by jamesisin on 2011-12-15
Sorry to barge in, but any grub guru want to take a crack at my little disaster?

[http://ubuntuforums.org/showthread.php?t=1890926](http://ubuntuforums.org/showthread.php?t=1890926)

---


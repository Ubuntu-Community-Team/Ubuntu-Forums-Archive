---
title: "Mount Filesystem for Writing from Live CD"
date: 2009-12-04
forum: General Help
---

### Post by danforward on 2009-12-04
In a nutshell, I cannot boot normally and I need to edit my grub configuration, so I booted to the Live CD to edit /boot/grub/grub.cfg. No matter what I try, it will not let me save. I have tried "Places -> 20 GB Filesystem" and mounting from the command line "sudo mount -w /dev/sda6 /media/sda6". And yes, I am using "gksudo gedit /media/sda6/boot/grub/grub.cfg".

The background is that I dual-boot Ubuntu 9.10 and Vista Home on my laptop computer. I made the mistake of formatting the Ubuntu partitions "/" and "/home" as ext4, which cannot be read from Windows, so I used rsync -avHXx to backup the two partitions to an external drive, used GParted from the Live CD to format the partitions as ext3, and then used rsync to restore the partitions. Now when I boot, it does not recognize the partition GUID in the grub menu, so I need to modify it.

---

### Post by Some Penguin on 2009-12-04
> **danforward said:**
> In a nutshell, I cannot boot normally and I need to edit my grub configuration, so I booted to the Live CD to edit /boot/grub/grub.cfg. No matter what I try, it will not let me save. I have tried "Places -> 20 GB Filesystem" and mounting from the command line "sudo mount -w /media/sda6 /dev/sda6". And yes, I am using "gksudo gedit /media/sda6/boot/grub/grub.cfg".

That mount command looks backwards.  Mount point goes after the device.

sudo mount -t ext4 -w /dev/sda6 /media/sda6

provided that /media/sda6 exists as a directory.

If it's already mounted (perhaps autodetected), but read-only, substitute '-o remount,rw' for -w.

The above assumes that the error given is that the filesystem is being mounted as read-only.

---

### Post by danforward on 2009-12-04
You are right about the mount command - I typed it in here backward, but correctly on the command line.

Now, for the real clincher: I just verified that the mount was read-write all along, but the file was read-only, even by root.

Solution: sudo chmod 644 /media/sda6/boot/grub/grub.cfg

Thank you for your help!

---


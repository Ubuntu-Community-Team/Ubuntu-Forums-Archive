---
title: "Accessing Wubi installed Ubuntu"
date: 2009-07-23
forum: General Help
---

### Post by ubuntubrian on 2009-07-23
I installed Ubuntu with Wubi and have a virtual dual boot. I filled the Ubuntu virtual disk when trying to recover an audio file and didn't empty the trash. Upon logging out and in I find the disk is full and I can't log in. I have tried many windows ways to access the Ubuntu virtual disk and delete some files to free up the space but to no avail.
I was able to run these commands and mount the virtual disk but I can't copy or delete any files: (fromthe WubiGuide) [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)


> How can I access my Wubi install and repair my install if it won't boot?

Boot the Ubuntu Desktop CD, or another LiveCD, then mount the windows partition:

sudo mkdir /win
sudo mount /dev/sda1 /win

Replace sda1 with the appropriate device (a = disk, 1 = partition number), then mount the virtual disk therein

sudo mkdir /vdisk
sudo mount -o loop /win/ubuntu/disks/root.disk /vdisk

Now the content of the virtual disk will be visible under /vdisk. 7.04 users will have to install ntfs-3g first and specify it as fstype to gain r/w access.

To check the filesystem you can use:

sudo fsck /win/ubuntu/disks/root.disk 

As I wrote, if I run nautilus as root I can copy and paste files into a USB drive but there are no files present when I open them even though the copy process occurred.
I figure that if i could somehow delete my trashed files I could free up enough space to boot in Ubuntu but I can't find the Trash either in Nautilus nor in a shell. (Where is the Trash in a shell with my Wubi/Ubuntu filesystem mounted anyway?)

Thanks for any help

---

### Post by ubuntubrian on 2009-07-25
I reran the same commands and found that I could use the mv command and the files stuck. I was able to clear enough space and boot into Ubuntu. I then ran LVPM and resized my Ubuntu virtual disk. Soon I'll attempt to move the Wubi install to a real partition but for now I have plenty of disk space.

---


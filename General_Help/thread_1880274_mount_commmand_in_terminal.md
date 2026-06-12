---
title: "mount commmand in terminal"
date: 2011-11-13
forum: General Help
---

### Post by mikhl on 2011-11-13
[FONT=Arial][SIZE=3]I am trying to mount my usb stick. The code that I have used so far is:  

[/SIZE][/FONT]```
mkdir /mnt/image 
mount -t fat32 /media/M-MURPHY /mnt/image
```[FONT=Arial][SIZE=3]

I am not using sudo as I am running in root

The error I am getting is:
[/SIZE][/FONT]```
[FONT=Arial]
mount: unknown filesystem type 'fat32'
mount: maybe you meant 'vfat'?[/FONT]
```[FONT=Arial][SIZE=3]

Does this support fat32?

On a side note, How would I mound a device in read only?

Thanks
[/SIZE][/FONT]

---

### Post by lswb on 2011-11-13
use "mount -t vfat". (run "man mount" and  "man fstab" in a termingal for more info) However, ususally systems will automatically mount USB drives, and the mount command is used with a device name, normally something in the /dev directory. Typically a mount command for a usb stick (if needed) would be something like 

mount -t vfat /dev/sdb1 /mnt/image

My guess is that your system has already mounted the USB drive at /media/M-MURPHY. Most removable drives are automatically mounted to a subdirectory created in /media at the time of mounting. If you do need to use a manual mount command, after plugging in the device, you can usually find the assigned device name by looking at the last few lines of output of the command "dmesg" or by looking at the end of /var/log/messages or /var/log/syslog. You'll see some lines about device discovery and probably something like "sdb: sdb1" on one of them.

---


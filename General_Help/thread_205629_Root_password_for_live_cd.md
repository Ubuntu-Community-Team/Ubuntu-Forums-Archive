---
title: "Root password for live cd"
date: 2006-06-28
forum: General Help
---

### Post by CrossGT6 on 2006-06-28
Pretty basic just need to know what the root password is for the live cd. I have the ppc version. 

Thanks

---

### Post by aysiu on 2006-06-28
You don't need to know the root password. Anything you execute with *sudo* doesn't require a password on the live CD.

---

### Post by CrossGT6 on 2006-06-28
Ok that worked but I am not good with mounting files. I am trying to mount a second partition on an external hd. 

This was the command I used:
sudo mount /media/usbdisk type ext3

I am not sure what to do as it again gave me more instructions and honestly... I have never mounted a drive image. I really need to mount to images. 

One is the internal HD image which is OS X but I have no problem formatting it to sa fat 32 which is pretty easy for all OS's to read. I just need to get the data on the external on to the internal as my external is a bigger drive and I want to use it as the main drive instead of the one already in there. (However I need the information to be transfered first). 

Thanks though for the sudo information I appriciate it!

---

### Post by J-Mann on 2006-06-28
Does this mean that the root password is not available - period?

---

### Post by thasheep on 2006-06-28
is the hd not mounted automatically? anyway, the "normal" mount command is

sudo mount /dev/sda2 /media/usbdisk

sda2 may not be the correct device so play around with that but usb drives are normally sd[a-z] ; the number refers to the partition number. /media/usbdisk is the mount point and it can be any directory that already exists (create it with mkdir if it doesn't). You can almost always forget about the type (common types are detected) however, if you must....

sudo mount -t ext3 /dev/sdb2 /media/usbdisk

Also, there IS no root password on k/x/ubuntu (live or otherwise) by default. If you want to get a normal root shell, do

sudo -i

If you want to create a root password to allow root login...

sudo passwd

However, ubuntu has taken the step of disabling the root account by default to force people to use sudo so that they'll think about whether they should do things as root. Using root unnecessarily is potentially dangerous.

---

### Post by CrossGT6 on 2006-06-28
Ok when I do the first command you suggested it tells me I need to tell it what file system type the parition is. 

When I try the second it says:
wrong fs type, bad option, bad superblock, on /dev/sdb2,
missing the codepage or other error
In some cases useful info is found in syslog - try
dmseg | tail or so

When I remove the -t I get:
Instructions that I am not sure what to do. They are basic instructions of how to mount but not basic enough for me I guess so I am again lost.

---

### Post by J-Mann on 2006-06-28
I understand and appreciate the value and purpose of sudo. 
For a server configuration, setting sudo up should be optional, not an out of box configuration. I appreciate your help and suggestions.

---


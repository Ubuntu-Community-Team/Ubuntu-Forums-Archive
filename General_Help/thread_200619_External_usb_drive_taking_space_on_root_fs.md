---
title: "External usb drive taking space on root fs?"
date: 2006-06-20
forum: General Help
---

### Post by eMcJagger on 2006-06-20
Hello,

First of all, I'm a newbie, so pardon my ignorance.

I'm trying to backup just my home directory onto an external usb hard drive.  I don't need any fancy compression or anything, just a straight recursive copy of my home directory and all its subdirectories so that I can reinstall Breezy and copy the contents back.  I followed these instructions to create a filesystem on a brand new "Safe Store" 250 GB external usb drive.: [http://www.thelinuxpimp.com/main/modules.php?op=modload&name=News&file=article&sid=561](http://www.thelinuxpimp.com/main/modules.php?op=modload&name=News&file=article&sid=561). Now I have a nice filesystem mounted at /mnt/usbdrive/ and it seems that I can read + write to it fine.

To copy over my home, I did this:

```

sudo mkdir /mnt/usbdrive/backup
sudo cp -r /home/jeremy /mnt/usbdrive/backup
```

It seemed to be working slowly but surely (files were appearing in /mnt/usbdrive/backup), but then I got warnings that my memory was low, and when I used the System > Administration > System Monitor tool, I noticed that the memory on / was indeed being eaten away bit by bit (so to speak) as the the copy proceeded.  I cancelled the copy and recursively removed /mnt/usbdrive/backup.

This doesn't make any sense to me.  Isn't the whole point of an external drive that  it *doesn't* take the space from your root filesystem?  Are my method and/or understanding flawed?

Any help much appreciated.

---

### Post by ape on 2006-06-20
What I don't see in your commands is where you actually mount the usb disk.  I see where you make the mount point and where you start copying files to that directory, but what was the mount command you used?

---

### Post by oscar on 2006-06-20
The drive was mounted as /mnt/usbdrive so it appears that it is "under" / (it is) and on the root partition (it isn't). I would just procede with the copy provided that you have enough space on your usb drive for your home dir. On a related note make sure that you unmount the usb drive instead of just removing it, otherwise data which has not yet been written to the disk is lost. Though the copy may show as finished but I think it is possible that the data has not all been written to the drive.

[EDIT] good point ape - make sure that the usb drive is mounted as /mnt/usbdrive. [/EDIT]

---

### Post by eMcJagger on 2006-06-20
Wow, thanks for the quick reply!

Here's the list of commands I did from a root terminal, starting with the brand new hard disk:

fdisk /dev/sda
mkfs.ext3 /dev/sda1
mkdir /mnt/usbdrive
mount /mnt/usbdrive

I also added this to /etc/fstab before the mkdir
/dev/sda1 /mnt/usbdrive auto user,noauto 0 0

EDIT:  Oscar:  Mm, that's the problem:  I *don't* have enough space for a whole other copy of my home directory!  I'm at about %89 of disk space now, an I believe most of that is my home.

So If I understand correctly, the OS thinks /usbdrive is part of the root filesystem because it is mounted under /, even though it is actually a separate filesystem.  Does this mean that every time I mount the external drive under /mnt, the OS will think whatever's on there is on the root FS and will cack out if it's too much?  I do expect to have more on the external drive than I can fit on the internal one -- again, that's why I bought it.  Is there another way to mount it that doesn't have this problem?

---

### Post by eMcJagger on 2006-06-20
Oops, I'm not sure exactly what happened last time but it seems to be working now.  I'm guessing I didn't mount the external drive properly and was just copying to a regular directory on mnt.  Currently, "cp -r /home/jeremy/ usbdrive/jerBak" is processing and I can see the progress in the system monitor:  /dev/sda1 is getting slowly fuller while /dev/hda1 is sitting pretty at 89%.  All is well.


Sorry for my confusion.

---


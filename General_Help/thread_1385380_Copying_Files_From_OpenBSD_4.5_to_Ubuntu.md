---
title: "Copying Files From OpenBSD 4.5 to Ubuntu"
date: 2010-01-19
forum: General Help
---

### Post by intermentals on 2010-01-19
I need to copy some files from an OpenBSD 4.5 server to my Ubuntu set up via flash disk

Could anyone tell me what commands to enter on each in order to do this please? I believe OpenBSD is UFS and I'm running 9.10 so Ubuntu is ext4

Thanks

---

### Post by tom4everitt on 2010-01-19
I think you need to describe your system setup in a bit more detail.

Is it two systems on the same computer, or is it two different computers for instance?

---

### Post by intermentals on 2010-01-19
it's a compaq rack mounted server machine with OpenBSD on and my eMachines E525 laptop with Ubuntu Server 9.10 32bit with the desktop packages deployed

The USB drive is a Sandisk Cruzer

---

### Post by tom4everitt on 2010-01-19
So would it work to just connect the usb drive to bsd, copy the files from bsd computer to usb drive, connect the usb drive to ubuntu computer, and copy them to ubuntu?

---

### Post by beowuff on 2010-01-20
So, are these computers not networked? If they ARE, you could use scp, sftp, rsync, wget, etc. to move the files. Why even bother with physical media?

If not, flash drives are usually formatted fat16 or fat32, so pretty much any computer should be able to read it. Even if you format it ext2 or ext3, both should be able to read it.

---

### Post by intermentals on 2010-01-20
__tom4everitt:

yes it would - however OpenBSD and Ubuntu use different file systems so I need to create a UFS partition in OpenBSD, mount it, copy the files to the disk swap to Ubuntu, get Ubuntu to see the UFS partition and view the files

---

### Post by intermentals on 2010-01-20
Beowuff:

I could hook the laptop up to the network with the OpenBSD server

what would the command line be (server is 192.168.1.3 and the directory is /etc/squid)

edit: I would prefer to use the wget command

---

### Post by tom4everitt on 2010-01-20
> **intermentals said:**
> __tom4everitt:

yes it would - however OpenBSD and Ubuntu use different file systems so I need to create a UFS partition in OpenBSD, mount it, copy the files to the disk swap to Ubuntu, get Ubuntu to see the UFS partition and view the files

I'm pretty sure you don't need to bother with this. As a previous poster said, any system will read a FAT-partitioned usb-drive. 

So simply:

mount it in OpenBsd:

mkdir /mnt/usb
mount -t vfat /dev/sdb1 /mnt/usb

Then copy the folder/files you need:

cp -r <folder-to-copy> /mnt/usb/

Then unmount:

umount /dev/sdb1
rmdir /mnt/usb

Then just plug it in in ubuntu and it should be automatically discovered and mounted.

---

### Post by beowuff on 2010-01-22
From Ubuntu box:

cd to where you want to copy the files.

scp -Cr <openbsd username>@192.168.1.3:/etc/squid/* ./

This will use ssh to copy the files over the network. -r is recursive. -C compresses the data stream, so it should run faster.

Personally, I prefer rsync, but you have to install it on each box. ssh (and thus scp) should already be installed.

rsync -rivP <openbsd username>@192.168.1.3:/etc/squid/* ./

-r is recursive. -i gives you information about what changed for each file (if it's new, the size change, the time stamp changed, etc.) -v is verbose (I like to watch the file copy process) and it gives you a summary at the end. -P is progress and gives you a progress bar as well as moving files in pieces. That way if it gets interrupted, it will restart from where it left off.

Also, remember. man is your friend. Try "man ssh", "man rsync", and "man scp".

---

### Post by intermentals on 2010-01-27
thank you both so much you're stars

---


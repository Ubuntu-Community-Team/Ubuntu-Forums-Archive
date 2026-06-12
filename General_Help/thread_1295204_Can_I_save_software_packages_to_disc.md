---
title: "Can I save software packages to disc"
date: 2009-10-19
forum: General Help
---

### Post by OfNoNation on 2009-10-19
I have a painfully slow internet connection (217kbps EDGE) and I was wondering if it's possible to save software packages from the repositories to my hard drive for storage and later installation.  With four computer to configure it would save me many hours waiting for the same stuff to download four times.

---

### Post by igknighted on 2009-10-19
The .deb for any package you have installed on your computer will be in /var/cache/apt/archive, unless you have run 'apt-get clean'.

---

### Post by OfNoNation on 2009-10-19
Thanks for the info.  Would they be in the same place if I use Synaptic?

---

### Post by howefield on 2009-10-19
> **OfNoNation said:**
> Thanks for the info.  Would they be in the same place if I use Synaptic?

Yep, that's where you'll find them.

---

### Post by jrev on 2009-10-19
I have a system by which I download the system and the updates only once, then I copy the downloaded packages on to a USB key.
I have another script to transfer the packages to another PC.
If you are interested I will let you know the details of the operations :P

I just moved to broadband with 3 to 6 PC's
my slow connection was 3 to 10 kbs  and the fast one downloads up to 125 kbs !

---

### Post by OfNoNation on 2009-10-19
That would be great, thanks, jrev.

---

### Post by jrev on 2009-10-20
this is the script to copy the packages from the updated PC to the USB disk :
> #!/bin/bash
SOURCE_DIRS=/var/cache/apt/archives/*.deb
TARGET_DIR=/media/disk/archives

# monter le repertoire disk
# mount /media/disk

rsync -av --del --stats --filter "- lock" --filter "- partial/" $SOURCE_DIRS "$TARGET_DIR"

#démonter /media/disk
umount /media/disk
echo "Transfert Terminé"

This is the script to copy the packages from the USB stick into the computer to update :

> #!/bin/bash
SOURCE_DIRS=/media/disk/archives/*.deb
TARGET_DIR=/var/cache/apt/archives/

# monter le repertoire disk
#mount /media/disk

rsync -av --del --stats $SOURCE_DIRS "$TARGET_DIR"

#démonter /media/disk
umount /media/disk

echo "Transfert Terminé"


you open a gnome console and drop the script into the console window so that it is executed  :)

Then you can use synaptic or the update system without problem

You have to create a folder <archives> on the USB key of course. and make the scripts executable.

---

### Post by snova on 2009-10-20
There is also APTonCD for this sort of thing.

---

### Post by jrev on 2009-10-21
Yes, I tried it. But you cannot use it on netbooks and you need to use rw CD's which are not very reliable:)

---

### Post by OfNoNation on 2009-11-09
Snova: I found APTonCD before I saw your post and tried it. It worked well and, for the record, I used a CD-R.  Thanks for the input.

jrev:  Thanks for the scripts... I'll be trying them later.  I have to install Ubu to 25 formatted, networked machines next week (internet cafe).  Would you know how the updates can be done from one updated computer on the network?  Perhaps I should start a new thread for that question. It's probably something like declaring the updated comp a server and setting the apt repository on all the others to that machine. Perhaps I should just skip town while the going's good!

Meanwhile, thank you for your help in my early stages of insanity.

---

### Post by kio_http on 2009-11-09
jst copy the .deb files and then in synaptic go in software sources and add a cdrom represitory

---


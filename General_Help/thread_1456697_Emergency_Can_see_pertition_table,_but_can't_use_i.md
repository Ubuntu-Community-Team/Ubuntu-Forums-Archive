---
title: "Emergency: Can see pertition table, but can't use it."
date: 2010-04-17
forum: General Help
---

### Post by DivadLarsen on 2010-04-17
So as the title suggests, I am in quite a pickle!

Short version: 
I ran "dd if=/dev/zero of=/dev/sda" on my harddrive - how do I access my partitions again?

Long (accurate) version:
I was making a bootable usb-stick, and as I pasted the command "dd if=/dev/zero of=/dev/sda" into the terminal, it was run automatically before I could change it to sdc1!

So basically I guess I tried to overwrite my harddrive with zeroes. BUT i booted an Ubuntu live-cd and ran the program testdisk, so I got my partition table back - I could even enter the partitions a see files and directories.

However, when I try to re-install Ubuntu/Debian it tells me the drive is empty - even though I can access a shell during installation an see the partitions with fdisk!

How do I get the actual partitions back?

---

### Post by srs5694 on 2010-04-17
I think you need to be more precise about what's happening. There's a script floating around that'll run a bunch of diagnostic tools and produce output you can post here. Unfortunately, I don't have a URL handy; maybe somebody else will see this and post it.

In the meantime, try posting the output of "sudo fdisk -lu"; that'll at least tell us where your partition(s) are on your disk. Also, how quickly did you cancel that dd operation? If it was just a second or two, chances are only one partition was trashed. If it ran for a long time, though, it could be most of your disk is completely wiped.

I suspect that what's happened is that you trashed the partition table in the MBR and part of the first partition. You've recovered at least part of your MBR using testdisk, and one or more other partitions may be OK. It may be difficult or impossible to recover files from that first partition, though, depending on how big it is and how long dd ran. If you can recover files, you might only do so using something like [PhotoRec,](http://www.cgsecurity.org/wiki/PhotoRec) which can recover individual files. If the first partition was your Linux root (/) filesystem, it will almost certainly be easier to re-install from scratch. If you have just one big filesystem for everything (system and user files), you might still want to run PhotoRec to recover as many of your user files as possible; but you might also end up wading through a lot of system files when you do so. This is, BTW, one of the big reasons for splitting off /home into its own partition. If your system was configured this way, and if /home was after root (/), your personal data files might at least be undamaged.

---


---
title: "Can't write Netbook Remix image to USB"
date: 2009-08-17
forum: General Help
---

### Post by mssever on 2009-08-17
I'm trying to write the Jaunty Netbook Remix image to a USB flash drive and having problems. First, I tried imagewriter. However, imagewriter invokes dd incorrectly. It tells dd to write to /dev/sdb, not /dev/sdb1. This hoses the partition table so badly that fdisk is the only tool that can cope with it (and fdisk reports numerous errors).

Since imagewriter is broken, I decided to manually invoke dd to write the image to /dev/sdb1. So far, so good. However, while I can see the files on the USB stick, I can't boot from it. Presumably there's more to making a bootable flash drive than invoking dd. What else do I need to do? (By the way, I've verified the md5sum of my image.)

Why isn't the remix shipped as an ISO? It's incredibly simple to write an ISO to a flash drive, so why use another format?

EDIT: I reported the following bug in imagewriter: [https://bugs.edge.launchpad.net/ubuntu/+source/usb-imagewriter/+bug/414406](https://bugs.edge.launchpad.net/ubuntu/+source/usb-imagewriter/+bug/414406)

---

### Post by fplum on 2009-08-18
Try this post from Ubuntu Forums:

[http://ubuntuforums.org/printthread.php?t=1065670]("http://ubuntuforums.org/printthread.php?t=1065670")

Let me know how it turns out because I am buying a flash drive Thur just for this purpose.

---

### Post by Mighty_Joe on 2009-08-18
The way I understand it, ISO files are CD images and IMG files are flash images. I don't know the difference.

From the [install instructions linked from the UNR download page]("https://help.ubuntu.com/community/Installation/FromImgFiles"):
> 
Command Line Interface

   1. Download the desired .img file
   2. Open a terminal and insert your flash media
   3. Look at the output of dmesg | tail -20 to determine the device node assigned to your flash media (ignore the device number; e.g. /dev/sdb, not sdb1)
   4. Run sudo umount /dev/device/node
   5. Run sudo dd if=/path/to/downloaded.img of=/dev/device/node bs=1M
   6. Remove your flash media when the command completes (you may need to wait a few extra seconds for it to finish) 

I think it is interesting that the instructions say to ignore the device number, whereas you used the device number.

---

### Post by F W Adams on 2012-07-06
Thanks Mighty_Joe, that fixed a problem I had.

Trying to write to a USB floppy with imagewriter it did not appear on the menu for the list of devices to write though other USB devices did appear.

However using dd worked fine.

--------------------------------------------

I think the reason for having to ignore the number, dev/sdc rather then /dev/sdc1, is because an iso or img file is associated with a (whole) device, not just a partition.

---

### Post by overdrank on 2012-07-06
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---


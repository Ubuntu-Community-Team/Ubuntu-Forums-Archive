---
title: "Help with formatting USB stick"
date: 2010-01-03
forum: General Help
---

### Post by datdaddy on 2010-01-03
I have a need for a USB stick to be formatted in a specific way for use with a DVR.

The instructions I got look like this below, but they don't seem to work on my ubuntu system.  I think they were written for another LINUX version.

Can someone take a look at this and tell me what these mean and how to get the same results in ubuntu?

Thanks so much.

Michael

Here are the directions I got ------------- :

Click on the TV screen type icon to open a command shell (Konsole)

Carefully type and enter the following

mkfs.ext3 /dev/sda1

Next step is optional it let's you give the drive a name the example calls it FoxsatBU

e2lable /dev/sda1 FoxsatBU

Now to set the partition type

fdisk /dev/sda

type t and enter

enter 83 at the prompt

type wq and enter

close the Konsole window

Click on the world icon and then media manager

Right click on the USB icon and choose safely remove

Remove the USB drive. Your foxsat should now recognise it and allow large file transfers.

---

### Post by HermanAB on 2010-01-03
It depends...

If the memory stick is small and you are not going to use it on Windows, then you don't need to partition it, so the minimum instructions become:

Plug it in:
$ dmesg
Note the device name, eg sdb

Wipe whatever is on it:"
$ sudo dd if=/dev/zero of=/dev/sdb bs=10M count=1

Format:
$ sudo mkfs.ext3 /dev/sdb

Bob's your uncle.

---

### Post by datdaddy on 2010-01-03
So the "83" and the "wq" are just meaningless in this case?

I am thinking that the device I'm using this one may require some of those optional parameters

Thanks.

---

### Post by 3rdalbum on 2010-01-03
Those commands need to be done with 'sudo' because they modify things outside your home directory.

And instead of "click the world icon and then media manager, right-click the USB icon and choose safely remove", just right-click the USB device on your desktop and choose Safely Remove.

---

### Post by datdaddy on 2010-01-03
> **3rdalbum said:**
> Those commands need to be done with 'sudo' because they modify things outside your home directory.

And instead of "click the world icon and then media manager, right-click the USB icon and choose safely remove", just right-click the USB device on your desktop and choose Safely Remove.

OK, I'm lost already.

When I do this:
$ sudo dd if=dev/zero of=/dev/sdk bs=10M count=1

I get this:

dd: opening `dev/zero': No such file or directory

Also, I think the parameter commands I mentioned earlier will need to be done somehow for this particular machine I'll be using this on, so can you explain how to do that once I get this part to work?  I think it would have been easier for me to understand if I knew what the parameters he mentioned actually meant, rather than just a "do this."

Anyway, I just used gparted to format the USB stick to ext3, which "seemed" to work fine,but when I put it in the PVR, it said it could only read FAT32 or EXT3 formats, so there's something it's wanting that's not quite right.  I have a feeling it's something to do with the "83" and the "wq"

Any ideas?

Thanks.

---

### Post by amsterdamharu on 2010-01-03
You are about to destroy your hard drive, do you have any idea what /dev/sda and /dev/sdb are?

Usually /dev/sda is your first hard drive if you have more than one then /dev/sdb is the second harddrive.

If you have only one harddrive chances are that your usb is /dev/sdb the first partition would be /dev/sdb1

So figure out what sd? your usb drive is by opening the drive in the file browser and then typing this command:

mount

This will get you a list of mounted drives (hard drive, usb and some loop stuff maybe)

If you know which one your usb is (for example /dev/sdb) than you can do:
fidisk /dev/sdb

press d enter to delete partitions untill all partitions are gone
press n for a new partition choose primary first partition.
press t to change the partitoin id to 83
press w to write changes and exit

Now format the partition:
mkfs.ext3 /dev/sdb1

You can try to label it but you need the e2lable program.

Note that in the example sdb should be changed to what your usb actually is (sda or sdb or sdc or whatever)

---

### Post by datdaddy on 2010-01-03
> **amsterdamharu said:**
> You are about to destroy your hard drive, do you have any idea what /dev/sda and /dev/sdb are?

Yes, the drive I want to format and use is an 8 gig stick for now.  It is sdk

> **amsterdamharu said:**
> If you know which one your usb is (for example /dev/sdb) than you can do:
fidisk /dev/sdb

press d enter to delete partitions untill all partitions are gone
press n for a new partition choose primary first partition.
press t to change the partitoin id to 83
press w to write changes and exit

Now format the partition:
mkfs.ext3 /dev/sdb1

You can try to label it but you need the e2lable program.

Note that in the example sdb should be changed to what your usb actually is (sda or sdb or sdc or whatever)

I'm assuming your "fidisk" is a typo and should be "fdisk" is that right? And everywhere sdb or sda is referred to will be sdk for me.

I'll try this and see.  Thanks so much for the reply.

m2

---

### Post by amsterdamharu on 2010-01-03
Yes the fidisk is a typo, sorry.

Change sdb and sdb1 with sdk and sdk1 that'll do.

---

### Post by datdaddy on 2010-01-03
Well, I finally got it to work.

I ended up using a CD of NimbleX to issue the commands and it worked perfectly.

I still don't really know what the commands "mean," but the PVR I was using recognized the newly formatted USB stick and I was able to archive video to it in sizes larger than the 4 gig limit.

Thanks for your input.

m2

---


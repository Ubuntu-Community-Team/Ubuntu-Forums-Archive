---
title: "Data recovery: New to ubuntu... had no idea about Debian-based /tmp clearing"
date: 2011-03-30
forum: General Help
---

### Post by emonti on 2011-03-30
Hi,

I have made the seemingly fatal mistake of leaving data in /tmp across reboots. It has been deleted.

I have used other linux distros(suse, redhat and mandrake/mandriva) and never encountered this before so even if you think it is a silly thing to do, one needs to be informed - the knowledge doesn't just arrive out of the ether. I'm pretty annoyed with this default Ubuntu maintenance policy. Perhaps I would be proved wrong but that debate is probably best left for another thread anyway. 

So the question now is whether it is possible for me to recover the deleted directory and if so how to recover the data. It is data that means an aweful lot to someone who trusted me with it so I really would be grateful for some help here.

I have read the following thread and have tried two of the three suggestions :

[http://ubuntuforums.org/archive/index.php/t-813442.html](http://ubuntuforums.org/archive/index.php/t-813442.html)

The two suggestions I tried are the use of testdisk and photorec. Neither have enabled me to retrieve the files I'm after. 

Perhaps it is because since the first reboot after storing the files in /tmp, I have downloaded files, in the size range of 30MB, regularly.

Anyway there is a third suggestion which I'd like to try but I'm not sure it is applicable to my situation exactly (hence the new thread).

My partition is type ext2. I have an external HDD 3TB so plenty of space to back up my drive/partition. But it's NTFS formatted so if I want to follow the advice in the linked post should I reformat a portion of the ext hdd in order to make a copy of the drive/partition?

For that matter is the advice beginning with the paragraph: 'The second option is one that I've had personal experience with. ...' valid to try with an ext2 fs?

Any help would be most appreciated as I've got myself into a bit of bad a situation here.:(

---

### Post by Duncan Williams on 2011-03-30
There are a few recover/undelete programs around.
Have a look around here:
[http://www.google.com/search?q=recover%20ubuntu](http://www.google.com/search?q=recover%20ubuntu)

---

### Post by lithopsian on 2011-03-30
Trying to recover files from an ext2 partition?  Good luck!  Doubly difficult if you have done much to the drive since then.

Making a complete back copy of the drive is to stop you overwriting any more data that might still be lurking on the disk.  As mentioned, it is probably about 10 boots too late for this, but you might as well put the data somewhere that you can work on it in peace.

You should copy the entire partition into a unformatted area of your external drive.  You are not copying files so you can't copy to an existing file system.  You must use the dd command to exactly copy each byte from the /tmp partition.  While you're at it, you might want to create a couple of extra empty partitions for attempts to recover the data.  You can certainly try these things with an ext2 partition.

---

### Post by emonti on 2011-04-01
Ok. Thanks, I will give it a go.

I need to first resize my NTFS partition ... but it seems GParted on Lucid cd boot, doesn't list my external usb device at all.

Any idea why that might be? I read somewhere that the device should be unmounted before it can be detected but it makes no difference - even after a device list refresh in GParted.

(I tried running the install/setup Windows software which came with the ext drive but there is no option for resizing it)

---


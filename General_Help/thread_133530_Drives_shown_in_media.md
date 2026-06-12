---
title: "Drives shown in /media"
date: 2006-02-20
forum: General Help
---

### Post by ajgreeny on 2006-02-20
This is not an important question as my machine works beautifully, but I think an answer would increase my linux/ubuntu knowledge.
In /media I have a floppy and floppy0, cdrom and cdrom0, and sda1, sdb1, and sdc1 drives showing.
Why are there two floppies, cdroms and three sdx1 drives showing.  If I load a cd the files seem to show up on both drives in /media, and the same for floppy disks.  As I say, it doesn't matter too much as everything works great, but I am just inquisitive.  Your answers would be much appreciated.

---

### Post by Neo Ex on 2006-02-20
What's the content of your /etc/fstab?

---

### Post by ajgreeny on 2006-02-20
Hi Neo Ex.

Here's my fstab file.  Perhaps I could just get rid of the zeros in the floppy and cdrom entries and mount on floppy and cdrom, not floppy0 and cdrom0 as it is at present, but I did not want to do anything that might break things that are working well.  You know the saying, "If it ain't broke, don't fix it!"

/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda1       /media/windows  ntfs    nls=utf8,umask=0222 0       0
/dev/hdb2       /media/suse	reiserfs   defaults	0	1

Don't work too hard on this; as I said everything works great, but I'm just curious.

---

### Post by Jucato on 2006-02-20
the /floppy and /cdrom directories, are just links to /floppy0 and /cdrom0, respectively. you can check where these links point to by typing "ls -l" (minus the quotation marks) on the terminal in the /media directory. In konqueror, you will notice that they have italicized names, meaning they are just links. No need to worry about this. Actually, don't modify this!

As for having sdx... I'm not entirely sure why they are showing there. sd- is the name given to SATA drives (hd- for ATA/IDE). Unless you have a SATA drive with 3 partitions, then I'm not sure why it is there.

---

### Post by ajgreeny on 2006-02-21
Hi Fenyx

I've investigated a bit further and found that the sd*x* drives are made when I plug in either my xd card reader for my camera cards or my Kingston 512Mb usb stick to the computer.

Why is it that the system beleives they are SATA drives and not usb?  They both also appear separately, the Kingston stick as "Kingston" and sde1 and the card reader as sdb1 and the card reader as "usb".  I'm completely bamboozled.  I trashed the folders in /media and when I plugged in the usb stick or card reader they were remade.  Very strange, eh?

Not to worry.  As I said before, "If it ain't broke, don't fix it!" and all works well!

---


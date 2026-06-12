---
title: "Need to move everything to another drive"
date: 2006-02-21
forum: General Help
---

### Post by DJStillman on 2006-02-21
Hey all:

Breezy user, currently running on 10GB IDE hard drive, 9GB formatted, 4GB Free.  Need the IDE drive for something else, so I need to move everything onto either a 9GB SCSI (Preferred drive), 8GB formatted, or an 18GB SCSI drive, 16.5GB formatted.

I have looked into several methods, such as DD (could not find much info), Partimage (don't want an image, just to move stuff over), some old linux site that used cp (could not get everything over fully), etc.

I know there has to be a way to fully clone the data to the next drive, but I have not found it.  If you have any ideas, please let me know.

Thank you.

David

---

### Post by cotcot on 2006-02-21
Question 3.1 of the FAQ of partimage explains a couple of thinks : [http://sourceforge.net/docman/display_doc.php?docid=15091&group_id=6212](http://sourceforge.net/docman/display_doc.php?docid=15091&group_id=6212)

I would use partimage for that; writing an image to a couple of DVDs (or even CDs) and placing it back to the new drive. The small one will do. For partimage the partition from where you make the image must be equal or smaller than the partition where the image will be installed.
Copy also the partition table and the MBR.
I have used it several times. The article [http://freshmeat.net/articles/view/1375/](http://freshmeat.net/articles/view/1375/) was very usefull to learn it.

---

### Post by KnottyMan on 2006-02-21
Just install the SCSI drive in the existing machine.  Fdisk it with the partitions sized the way you want.  Then mkfs on the partitions.  mkswap on your swap partition.  : )

Then mount the root pattion somewhere and cp -av.  Get everything copied over.  Yank the old IDE and then boot the ubuntu CD in rescue mode and do a grub install to the SCSI's mbr.  grub-install /dev/sda

You will probably have to tweak fstab switching from hda to sda.  Might also have interesting time with getting the SCSI HBA to get it loaded in initramfs image.

This is how I've always transferred.  Or reinstall...

---

### Post by Fred Doolie on 2006-02-21
That answers one of my questions too. When I dump Winblows 100% I'll want to delete my HDA1 (Win2000), resize HDA2 (Ubuntu) to the entire drive (plus the swap) and then reinstall Ubuntu WITHOUT having to start over from scratch.

Or.....will that part utility resize without losing data? Then I'd just have to edit menu.lst to reflect the changes.

---


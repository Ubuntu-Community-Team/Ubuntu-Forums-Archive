---
title: "How do I make nautilus show the &quot;name&quot; of the disk?"
date: 2009-08-04
forum: General Help
---

### Post by harrybazeegar on 2009-08-04
Hi,

First thing: the title of the question does not describe everything, really...

I've attached an image, and I'll explain my question with its help.

I have mounted an ext3 formatted partition on /media/stuff (see the first read circle).

I've added an fstab entry to mount it automatically everytime I start my computer. The entry reads:

```
/dev/sda6   /media/tinger    ext3    relatime,auto,user      0   0
```

Now, in nautilus, this drive shows up as "50.0 GB Media" (second red circle), while I want it to show up as "stuff".

My questions:
1. Can it be done?
2. If yes, how?
3. Does this have something to do with the "drive label"?
4. what exactly is the drive label?
5. do ext3 partitions have drive labels?

Thanks :) ,
jrh

---

### Post by damis648 on 2009-08-04
> 1. Can it be done?
Sure.
> 2. If yes, how?
If I recall correctly, all you need to do is rename it in nautilus. Right click > rename. (I am not on ubuntu at the moment, so I can´t say for sure... i am pretty sure ext3 supports naming just as NTFS and whatnot, and I beleive nautilus can do it. ... forgive me if I am wrong)
> 3. Does this have something to do with the "drive label"?
Nope.
> 4. what exactly is the drive label?
Provided you are referiing to what gparted referrs to as the drive label, the drive label is the type of partition table the disk (the whole disk, not partition) has. This can be MBR, GPT, etc.
> 5. do ext3 partitions have drive labels?
They are for entire disks, not partitions as stated above.

---

### Post by harrybazeegar on 2009-08-04
Hi, the rename option is not available on the drive list... but wait! Look what I discovered:

When I run nautilus with sudo ("sudo nautilus"), the mount point names are coming up instead of "50.0 GB Media"!

what's that, now? does that indicate something? Am I missing something obvious?

---

### Post by Andreas1 on 2009-08-04
yes, that would be the drive label.

you can set the label of an ext3 partition with "e2label" (open a terminal and type "man e2label" and it will explain) or use the partition editor gparted to set the label if you prefer a gui way.


EDIT: i am sorry, not a DRIVE label but a FILESYSTEM label is what that is.

try ```
sudo e2label /dev/sda6 stuff
```
not sure though if the changes take effect immediately in nautilus or after logout and in again.

---

### Post by harrybazeegar on 2009-08-04
@Andreas1 are you sure filesystem label is the right solution?

I remember one time when I tried applying a label to something using gparted.. and all the data on the drive was zapped out.

Is the operation safe?

---

### Post by Andreas1 on 2009-08-04
> **harrybazeegar said:**
> @Andreas1 are you sure filesystem label is the right solution?
yes.

every partition/filesystem can have a label, you could even use the label to identify the drive in fstab:
```
LABEL=stuff   /media/tinger    ext3    relatime,auto,user      0   0
```

> **harrybazeegar said:**
> I remember one time when I tried applying a label to something using gparted.. and all the data on the drive was zapped out.

Is the operation safe?

i am pretty sure its safe, personally i would use e2label because its designed specifically for this purpose while gparted is a weapon of mass destruction (although it should be just as safe if you double check your actions before you click apply).

[here]("http://ubuntuforums.org/showthread.php?t=283131") is a good thread about fstab, there is also a section about labels, search for "How To Label"

---

### Post by kpkeerthi on 2009-08-04
Labeling partition is safe. [https://help.ubuntu.com/community/RenameUSBDrive]("https://help.ubuntu.com/community/RenameUSBDrive") (although it reads USB, it applies to non USB partitions as well)

---

### Post by harrybazeegar on 2009-08-04
Thanks a lot, e2label did the trick. 

and yes, it did not destroy any data i loved :)

thanks

---


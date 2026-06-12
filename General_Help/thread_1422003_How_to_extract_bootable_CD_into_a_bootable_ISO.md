---
title: "How to extract bootable CD into a bootable ISO"
date: 2010-03-04
forum: General Help
---

### Post by smmalmansoori on 2010-03-04
I own a legit Windows XP Home CD, with time its getting more scratches so I want to make an ISO backup. I tried Brasero but the ISO it creates doesn't seem to be bootable.
I don't mind using GUI programs, but I'd prefer to know the command line programs to learn more :). Any help appreciated!

---

### Post by labinnsw on 2010-03-11
An ISO image is not usually bootable unless it is burned onto a disc or it is treated as a virtual disc e.g. in Virtualbox, Qemu or VMWare. It is not clear from your post if you tried any of these.

---

### Post by smmalmansoori on 2010-03-16
> it is treated as a virtual disc e.g. in Virtualbox, Qemu or VMWare.

I am trying to make a backup copy of the CD, as well as using it as a virtual disc for VMWare Workstation since I don't want to dual boot anymore.

---

### Post by labinnsw on 2010-03-18
> **smmalmansoori said:**
> I tried Brasero but the ISO it creates doesn't seem to be bootable. 

> **smmalmansoori said:**
> I am trying to make a backup copy of the CD, as well as using it as a virtual disc for VMWare Workstation since I don't want to dual boot anymore.

Did you try to boot a VMWare Virtual machine using the image you created as the CD ROM?

If booting was successful in VMWare, did you burn the image to a CD?

After burning the image to a CD, did you try to boot your computer from the CD you burned?

---

### Post by lordskid on 2010-03-18
did you try to dd the cd into a file?

---

### Post by smmalmansoori on 2010-03-21
> Did you try to boot a VMWare Virtual machine using the image you created as the CD ROM?
I did, it wasn't recognized as a bootable image.

> If booting was successful in VMWare, did you burn the image to a CD?

After burning the image to a CD, did you try to boot your computer from the CD you burned?

I don't see why I would need to do that since all I need is an image backup.

> did you try to dd the cd into a file?
Do you mean to extract the CD's data normally into a file then convert the file into an ISO? That I didn't try, but might as well give it a shot.

---

### Post by labinnsw on 2010-03-22
> **smmalmansoori said:**
> I did, it wasn't recognized as a bootable image.
If this does not work, you can skip the rest.

Command line is good when we know how to use it, but failing that, there are still some other great GUIs that you could try. My next recommendation is K3b.

> **smmalmansoori said:**
> I don't see why I would need to do that since all I need is an image backup.
You also posted:
> **smmalmansoori said:**
> I am trying to make a backup copy of the CD
Please note the difference "an image backup" vs "a backup copy of the CD."

---

### Post by pbrane on 2010-03-22
I have created images like this:
```

dd if=/dev/sr0 of=winxp.iso

```

this will create an exact copy of the CD/DVD in iso format. Change */dev/sr0* to your CD/DVD device if you need to. You can find out where the CD/DVD is by typing *mount* in a terminal. You can burn this to disc using the CD/DVD creator in Nautilus. Or probably using Brasero to burn an image.

---

### Post by labinnsw on 2010-03-24
> **pbrane said:**
> I have created images like this:
```

dd if=/dev/sr0 of=winxp.iso

```

this will create an exact copy of the CD/DVD in iso format. Change */dev/sr0* to your CD/DVD device if you need to. You can find out where the CD/DVD is by typing *mount* in a terminal. You can burn this to disc using the CD/DVD creator in Nautilus. Or probably using Brasero to burn an image.

Lovely. I too have added this to my list of commands. Just one note; cd to the directory where you want the image to be created first. This is to save you having to move it.

---

### Post by smmalmansoori on 2010-05-17
Thanks all for the help, the dd command is working :)

---

### Post by elliotn on 2010-05-17
brasero works just change the extension to .iso.

---

### Post by sedawk on 2010-05-17
There is a command line tool "isoinfo" which I use
to get additional info from a CD.
E.g. block size (2048 bytes?) and number of blocks.

E.g. sometimes dd would return an error when reading
like you do above.
Then you have to tell dd when to stop. 
```

dd if=/dev/sr0 bs=2048 count=245897 of=copy.iso

```
When archiving isos I actually save 2 files,
the cdXYZ.iso and cdXYZ.info which is the output
from isoinfo.

---


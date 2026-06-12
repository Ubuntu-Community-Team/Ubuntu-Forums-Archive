---
title: "Floppys on Winimage wont work"
date: 2009-07-07
forum: General Help
---

### Post by Lingonet on 2009-07-07
Hello!

I am using Winimage via Wine and trying to make a bootdisk on a floppy. I'm going to try to install Windows 95. Anyway, whenever I try to write, format or even read I get one error message after another. When I try to format I get this error message:

```
The current image format is not supported by the disk drive
```

And when I try to read the disk:

```
The floppy cannot be accessed.
Please check if another application is using the floppy drive.
```

I followed someones guide in this thread how to set up the disk drive:

[http://www.linuxquestions.org/questions/linux-hardware-18/ubuntu-8.1-wont-use-the-floppy-disk-drive-681634/](http://www.linuxquestions.org/questions/linux-hardware-18/ubuntu-8.1-wont-use-the-floppy-disk-drive-681634/)

I don't have any problems with reading the disk in the "Places> Computer", so I don't know what the problem is.

I would be glad if someone could help me with this!

Thank you in advance!

-Lingot

---

### Post by Lingonet on 2009-07-07
Any ideas?

-Lingot

---

### Post by Jebtrix on 2009-07-07
Goto Wine > Configure Wine > Drives > Select Autodetect

In the drive list you should have, Letter A:, Path: /media/floppy, Type Floppy Disk.

Restart WinImage and try again.

---

### Post by Jebtrix on 2009-07-07
BTW /media/floppy0 is fine also, /media/floppy is just a sym link to floppy0 anyway.

---

### Post by Lingonet on 2009-07-08
> **Jebtrix said:**
> Goto Wine > Configure Wine > Drives > Select Autodetect

In the drive list you should have, Letter A:, Path: /media/floppy, Type Floppy Disk.

Restart WinImage and try again.

For me it says /media/disk. And where did you mean I should type "Floppy Disk"?

Thanks!

-Lingot

---

### Post by Jebtrix on 2009-07-08
If you have a floppy inserted it should come as floppy or floppy0. When you click autodetect in Drives tab you should see /media/floppy for path. It should assign A: letter to it. There should be an Advanced button, if you click it you will see the Type dropdown menu that will have Floppy disk.

---

### Post by t4thfavor on 2009-07-08
Do you have a raw image to write to the fdd? If so just use dd, it works much better than winimage though only if you have the actual floppy image.

---


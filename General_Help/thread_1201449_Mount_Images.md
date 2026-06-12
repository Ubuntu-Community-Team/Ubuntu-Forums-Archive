---
title: "Mount Images"
date: 2009-07-01
forum: General Help
---

### Post by mthalis on 2009-07-01
I want to mount images like .iso, .bin is their any software? also i want to create virtual cdrom, in widows i found good software like powerISO, MagisISO, these software satisfy both my above requirement. Any open source software available?
 
Thank You

---

### Post by sedawk on 2009-07-01
Mounting iso files with Linux is very easy and does not require
any extra software:

```

sudo mkdir /mnt
sudo mount -o loop /home/user/mydisk.iso /mnt
# or sudo mount -t iso9660 -o loop /home/user/mydisk.iso /mnt

```
This is a very simple solution but it does not simulate a
real CD-ROM drive. 

To mount other image formats (.bin) or to really emulate
a CD-ROM drive there is a nice project for Linux called "cdemu".
[http://cdemu.sf.net](http://cdemu.sf.net)

BTW: The best tool for windows I know is free "Daemon Tools".

---

### Post by niteshifter on 2009-07-01
Hi,

If you want to mount iso without the typing (command-line) there's Gmount-iso:
```
sudo apt-get install gmountiso
```
or get it via Synaptic. After installing look in Applications -> System Tools.

---

### Post by mthalis on 2009-07-01
Is it support for .bin format?

---

### Post by colau on 2009-07-01
> **mthalis said:**
> Is it support for .bin format?
I think no.

---

### Post by mthalis on 2009-07-01
Any solution?

---

### Post by colau on 2009-07-01
> **mthalis said:**
> Any solution?
[https://www.linuxquestions.org/questions/linux-software-2/extract-bin-files-57852/#post293798](https://www.linuxquestions.org/questions/linux-software-2/extract-bin-files-57852/#post293798)
[http://www.computing.net/answers/linux/extracting-bin-files/24446.html](http://www.computing.net/answers/linux/extracting-bin-files/24446.html)

---

### Post by mthalis on 2009-07-01
Any Options?

---

### Post by geirha on 2009-07-01
[http://wiki.linuxquestions.org/wiki/CD_Image_Conversion](http://wiki.linuxquestions.org/wiki/CD_Image_Conversion)

> mount-iso-image (EL) for the KDE Desktop ([www.kde.org](www.kde.org)) might also be of interest to you. Also, CDemu (EL) might be something to check out. Both programs can mount .bin/.cue images to a Virtual Drive, much like the Windows program Daemon Tools (EL) can. For a full program that can convert many images and do much much more, download AcetoneISO (EL) software. Yet another program that shows promise is IAT (EL).

---

### Post by colau on 2009-07-01
> **mthalis said:**
> Any Options?
Did you run this?
```

sudo mount -t iso9660 -o loop /home/user/mydisk.bin /mnt

```

---

### Post by valantis1985 on 2009-11-21
and if the iso is not 9660 (wain i try to open it with archiver is say "CD-ROM is NOT in ISO 9660 format" )what i can do?

---


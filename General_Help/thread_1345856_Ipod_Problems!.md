---
title: "Ipod Problems!"
date: 2009-12-04
forum: General Help
---

### Post by smithpercussion on 2009-12-04
So somehow my ipod got formatted. I need to get it to a format that rockbox will accept and be able to install. I can't open up gparted. As soon as it scans /dev/sdc it just auto closes. Is there a way to format through terminal. This is what I have already tried with my return. I am pretty sure this is how you do it but I am not 100 percent sure /dev/sdc is even the right file system but because my computer can't really read this linux formatted usb device I don't really know how to tell which one it is.

```
sudo mkfs.msdos /dev/sdc
mkfs.msdos 3.0.3 (18 May 2009)
/dev/sdc: No such file or directory

sudo mkfs -t vfat /dev/sdc
mkfs.vfat 3.0.3 (18 May 2009)
/dev/sdc: No such file or directory

```

Any ideas would be great! I really don't want to purchase a new ipod.

---

### Post by khelben1979 on 2009-12-04
I know that [Songbird]("http://en.wikipedia.org/wiki/Songbird_%28software%29") has a addon (not by default) which enables your Ipod to be read from it. Maybe you should try that instead? And if the filesystem of the Ipod have gotten corrupted in some way, maybe you can format it on a Windows system instead and then go back to Linux?

---

### Post by StuartN on 2009-12-04
> **smithpercussion said:**
> Any ideas would be great! I really don't want to purchase a new ipod.

I think it is strongly recommended to format an iPod using iTunes using a Mac or Windows. There is quite a good article at [http://www.linuxjournal.com/article/9266](http://www.linuxjournal.com/article/9266)

---


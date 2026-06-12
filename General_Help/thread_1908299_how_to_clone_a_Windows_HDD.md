---
title: "how to clone a Windows HDD?"
date: 2012-01-13
forum: General Help
---

### Post by F.G. on 2012-01-13
hi folks,

i need to clone a Hard Disk drive for a friend of mine, he wants a backup and is insistent that he wont selectively choose what to copy.  so, how shall i do this? (it's important as there is free beer in it for me).
 the computer is a Sony Vaio with windows7 (or maybe xp) on it.

my thoughts are to boot into a live usb version and then to used:
```
dd if=whereeverC:is of=/dev/sdb(or whatever the external drive is)
```
or something like that.

is this a good plan?? will it work? will the drive then be bootable? if so does this count as copyright infringement? (i assume for backup purposes this would still be legit).  if this wont work does anyone have any suggestion for how to clone this drive? either from a live usb or from inside windows itself.

thanks for all suggestions and any help with this issue.

---

### Post by kansasnoob on 2012-01-13
Windows typically will NOT run on a USB drive if that's what you're trying to do, but this link works for me if copying to a new internal drive:

[http://www.nilbus.com/linux/disk-copy.php](http://www.nilbus.com/linux/disk-copy.php)

It's easy to break things doing this :o

---

### Post by satanselbow on 2012-01-13
Have a look at **clonezilla**. It comes as a bootable iso and has a few compression / partition tricks up it's sleeve ;)

Very much depends whether you really need a slot in replacement drive or a compressed backup to restore ;)

If you are the owner of the drive there is no problem storing a backup - attempting to use the clone drive at the same time as the original is a different kettle of kippers however and may cause a problem depending on the contents of the drive :(

---

### Post by cryptotheslow on 2012-01-13
Use the built-in Windows 7 backup image tool :confused:

Although that likely won't see any manufacturer recovery type partitions - so maybe dd is better after all :)

---

### Post by F.G. on 2012-01-13
> **kansasnoob said:**
> Windows typically will NOT run on a USB drive if that's what you're trying to do, but this link works for me if copying to a new internal drive:

[http://www.nilbus.com/linux/disk-copy.php](http://www.nilbus.com/linux/disk-copy.php)

It's easy to break things doing this :o
thanks for your reply.  whether it can run via USB is not really important, i mean it would be nice to be able to boot it up, and to see it working, but the purpose of the disk is only to serve as a backup (therefore access via usb is important, but the only time it might need to be booted is if it had to be swapped out for the original, if the original failed). 

the same guy owns both disks (and only has one computer), so i think it should be ok.

---

### Post by F.G. on 2012-01-13
> **cryptotheslow said:**
> Use the built-in Windows 7 backup image tool :confused:

Although that likely won't see any manufacturer recovery type partitions - so maybe dd is better after all :)
ok, this could be a good solution. does it also copy personal files as well as the system? (does it only copy personal files and NOT the system?).

thanks for all your replies.

---

### Post by satanselbow on 2012-01-13
> **cryptotheslow said:**
> Use the built-in Windows 7 backup image tool :confused:

To create a backup - not a bit perfect clone ;)

If you want to do it from Windows you would get more mileage (flexibility in restoration) in using something like EASUS Todo Backup which is a freebie ;)

---

### Post by F.G. on 2012-01-13
thanks satanselbow, this could be a better solution.

no word on using the dd command? or copying it using linux?

---

### Post by C.S.Cameron on 2012-01-13
```
dd if=/dev/whereeverC:is of=/dev/sdb(or whatever the external drive is)
```

Has always worked for me with Windows.

---

### Post by kansasnoob on 2012-01-13
> **satanselbow said:**
> To create a backup - not a bit perfect clone ;)

If you want to do it from Windows you would get more mileage (flexibility in restoration) in using something like EASUS Todo Backup which is a freebie ;)

+1!

That sounds like a great fit in this case :D

---

### Post by Double.J on 2012-01-13
Just to clarify it you have only windows, then use the windows tool - just make sure that you have a recovery cd - it'll ask you to make one when you start the back up. 

dd is a great tool, but much more time consuming, it'll just make an exact bit for bit copy of the hard drive - a true clone, it'll take quite a while, and realistically only worth the effort I'd have thought if you're multibooting as windows will only back up windows partitions with the imaging tool.

CloneZilla is a good suggestion - it does the same thing as dd; I think it actually uses dd recscue, but I can't be sure as I don't use it. Also you'd have to use a live cd NOT an installation of linux to image a hdd using dd.

That said, in the interests of opptions, the dd command you most likely wanted was something like
```

sudo dd if=/dev/sdX conv=sync,noerror bs=32k of=/path/to/newimage.img

```
This would create the image as an .img file on a computer that you could then tarball to save space (if you archive a hdd image on linux you should always use tar instead of just g/b zip :) the arguments conv=sync,noerror & bs=32 tell it to write something in  the case of a faulty sector it'll write data anyway, making your image more reliable, and the bs, block size - for the most exact copy, you could set it to 1 but in the real world thi'll take for ever on a huge drive and offeres no real world advantage - People seem to use anything from 1 to 512 (most common are 32 or 64) 

N.B that command would have to be run from a live CD anyway... Which is why most people use clonezilla for this purpose as the minimal graphic display makes errors less likely - say you stored quite a few images on a drive, or worse a bunch of images for different machines - with dd you could accidentally mess up the syntax and copy a hard drive image for one machine OVER one you were trying to back up :(

---

### Post by Mark Phelps on 2012-01-13
I recommend using the FREE version of Macium Reflect to make an image backup of the Windows drive.  I use MR all the time on Windows systems and have never had any problems with it.

---

### Post by dcstar on 2012-01-16
> **gnu/mirow said:**
> 
...........
That said, in the interests of opptions, the dd command you most likely wanted was something like
```

sudo **dd** if=/dev/sdX conv=sync,noerror bs=32k of=/path/to/newimage.img

```
...........

**ddrescue** is a far superior choice than using **dd**, you get progress displayed so you have some idea when the job will be complete (along with a lot of other goodies).

---

### Post by F.G. on 2012-01-17
thanks for all your replies, and i'll take them all into account in future when similar issues occur. this time it turned out that my mate had already done the backup, and in fact wanted me to install windows7 (which i duly did and was compensated handsomely with much wine and a second-hand iphone).

thanks again for all the suggestions and advice.

---


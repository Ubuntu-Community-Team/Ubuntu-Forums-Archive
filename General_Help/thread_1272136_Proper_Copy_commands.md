---
title: "Proper Copy commands"
date: 2009-09-21
forum: General Help
---

### Post by xi_Slick_ix on 2009-09-21
Little command line question.  Been googling for several hours to no avail, so I figured I would just ask.

Trying to copy a folder form an external hard drive to my ubuntu NAS server.

the folder is located on ```
/dev/sda2
``` and is called ```
/sharemedia
```

the external is ```
/dev/sdb1
``` and is in a folder called "media"

i've tried the following:
```
sudo cp -R /dev/sdb1/media /dev/sda2/sharemedia
```

and that didn't work

then did the following:
```
sudo mount /dev/sdb1 /media
sudo cp -R /dev/sdb1 /media /sharemedia/david
```

this is a rather large file, and the drive's external case doesn't do the greatest job telling you whats happening, but is pulsing.

so does his seem correct?

---

### Post by i.r.id10t on 2009-09-21
Your first commands wont work - you are referencing the device file.

But, you mounted them, so thats good.

Your last command is copying the /dev/sdb1 device file (tiny thing) and the /media directory and all of its contents into /sharedmedia/david

---

### Post by CatKiller on 2009-09-21
> **xi_Slick_ix said:**
>  so does his seem correct?

No.

The /dev/sd*whatever* are block devices. They are a means to refer to the device itself, without any regard to what they actually are and, in particular, what's on them.

You're interested in doing things to the files that are on those devices. You access those files through the mount point. That's pretty much the point of mounting them (incorporating those files into the rest of the filesystem tree).

You'll need to copy the files from and to wherever you have those partitions mounted. I wouldn't recommend mounting to just /media. /media/*somedescription* would be a better plan, and will stop you messing up the other things that might also be mounted under /media, such as /media/cdrom.

/media is the [traditional]("http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard") mount location for removable media, such as cd-roms or floppy disks. /mnt is the traditional mount location for temporary-but-fixed media, such as hard drives. In practise, on Ubuntu, the main difference is that things mounted under /media get an icon on the desktop while things mounted elsewhere don't.

You'll probably find it much easier to do all your file-copying operations in the file manager. If you need to do so as root, you can start the file manager as root with ```
gksudo nautilus
```

---

### Post by xi_Slick_ix on 2009-09-21
Thank you for the information!

Yea I need a new word - on my windows systems I have been using the word 'media' as a common name for folders containing movies, music etc.  Clearly that word is not quite as effective here.

So then next time I come across this situation (assuming the 'media' folder on the external drive is now named 'multimedia' or something and is still located on /dev/sdb1) and I want to copy the contents of "multimedia" to "sharedmedia/user" would it look like this??

```
sudo mount /dev/sdb1 /multimedia
sudo cp -R /multimedia /sharemedia/user
```

---

### Post by CatKiller on 2009-09-22
> **xi_Slick_ix said:**
> So then next time I come across this situation (assuming the 'media' folder on the external drive is now named 'multimedia' or something and is still located on /dev/sdb1) and I want to copy the contents of "multimedia" to "sharedmedia/user" would it look like this??

```
sudo mount /dev/sdb1 /multimedia
sudo cp -R /multimedia /sharemedia/user
```

Whatever works for you.

```
sudo mount /dev/sdb1 /mnt/multimedia
``` or 
```
sudo mount /dev/sdb1 /media/multimedia
``` would be more traditional, though, with sharemedia also mounted under /mnt or /media as you see fit.

The names of folders on the partition don't matter at all. So if there were folders called *foo* and *bar* on that drive, when you'd mounted that partition (using the above example) you'd find them at /mnt/multimedia/foo and /mnt/multimedia/bar.

---


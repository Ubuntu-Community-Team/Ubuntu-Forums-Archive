---
title: "Howto fsarchiver: restoring a full partition archive to a mountable image"
date: 2010-01-14
forum: General Help
---

### Post by jchedstrom on 2010-01-14
Restoring an entire archived partition is wonderfully easy with fsarchiver, but recently I needed only a single file from an archive and had no free partitions to restore to. After failing to find any instructions to mount the *.fsa image directly I came up with the following method which may come in handy for other novices out there.

Note: this how-to is for those with a *.fsa created using '*fsarchiver **savefs** ...*' . From now on I will be using 'fsarchiver savedir ...' on my home directory instead, which will greatly simplify restoring single files.

From the man page on fsarchiver:
>        fsarchiver  is  a system tool that allows you to save the contents of a
       filesystem to  a  compressed  archive  file.  The  file-system  can  be
       restored  on  a  partition  which  has  a  different size and it can be
       restored on a different file-system. Unlike  tar/dar,  FSArchiver  also
       creates  the filesystem when it extracts the data to partitions. Every&#8208;
       thing is checksummed in the archive in order to protect  the  data.  If
       the  archive is corrupt, you just loose the current file, not the whole
       archive.Ultimately, I don't believe there currently is a way to directly mount a fsarchiver saved filesystem. Instead we will create an image file, restore the archive to this image, and then mount the image which will give direct access to the files. 

Step 1) Create an empty image for the restoration. Remember that the *.fsa is compressed and will expand somewhat. For example, my 10GB archive expanded to 15GB after this step. Make sure the image is large enough to accommodate the full restoration!
```

$ ls -lh home_fsarchiver_backup.fsa  #check the size of the archive
$ df -h  #check the free space on accessible drives, choose a location
$ dd if=/dev/zero of=home.img count=20 bs=1G  #create an empty 20GB image
```Step 2) Setup a loop device for the empty image and restore the archive to it.
```
$ sudo losetup -f  #check for unused loop back devices to use
/dev/loop0
$ sudo losetup /dev/loop0 homefsa.img  #setup a loop device
$ sudo fsarchiver restfs home_fsarchiver_backup.fsa id=0,dest=/dev/loop0
```Step 3) Mount the image of the restored archive.
```
$ mkdir tmp
$ sudo mount /dev/loop0 tmp
```Congratulations! You should now have access to all of your archived files on 'tmp'.

Step 4) Since we're running linux and don't believe in restarting our machines we should cleanup after manipulating our files.
```
$ sudo umount tmp  $ un-mount the image
$ sudo losetup -d /dev/loop0  #remove connection between homefsa.img and loop device
$ rm  -r tmp homefsa.img  #delete tmp and that giant image
```

---

### Post by molafish on 2010-10-31
For determining the neccesary partition size, use ```
fsarchiver archinfo [imagename].fsa
```

---

### Post by jaXvi on 2011-07-12
ehlo,

Interesting post, it was useful for me some months ago, return now to this topic by chance and here is my 2 cents.

You could create the empty (really empty, try df before and after) image file (e.g. 5 GB sparse file like) instantly doing:

dd if=/dev/zero of=4loopimg.img bs=1 count=0 seek=5G

Let's check with ls -l and du -s -B1

Thinking about programing something like "fsaexplorer" to automount and explore fsa backups. I'll see after summer :)
.

---


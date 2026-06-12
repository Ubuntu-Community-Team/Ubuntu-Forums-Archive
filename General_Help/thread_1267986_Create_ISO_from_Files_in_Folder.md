---
title: "Create ISO from Files in Folder"
date: 2009-09-16
forum: General Help
---

### Post by SnarlSlayer on 2009-09-16
OK, I've searched, I've tried, but no dice.

I want to create an ISO Image that includes all the files in a folder.
I've tried various commands I've seen on the net, but nothing seems to work.

The idea is that I have some files in a folder and one of those files is a windows auto.exe.  I want to create the ISO and then when someone burns the ISO onto a disk (CD or DVD), all the files are there, but not in a folder.

Please. It would make my life so much easier. 

SS

---

### Post by ChumleyEX on 2009-09-16
See if you have a burning app that allows you to burn an image.. You want that image.

---

### Post by sisco311 on 2009-09-16
You can use almost any burning up to burn an image.

From a terminal:
```
mkisofs -o filename.iso /path/to/dir
```

After the iso is created, you can mount it:
```
sudo mount -o loop filename.iso /mnt
ls /mnt
```

---

### Post by 3rdalbum on 2009-09-16
> **SnarlSlayer said:**
> OK, I've searched, I've tried, but no dice.

I want to create an ISO Image that includes all the files in a folder.

How odd, I was just working with this today in a script I wrote.

You want the *genisoimage* command:

```
genisoimage -o output.iso /home/chris/important-directory
```

That will create a pure ISO9660 filesystem. If you wanted a different sort of filesystem, or if you wanted to create a video DVD filesystem, then consult the *genisoimage* man page.

---

### Post by geirha on 2009-09-16
For the graphical approach, start Applications -> Sound & Video -> Brasero Disc Burner.

Select Data project, drag over the files and folders you want on the image, then hit the burn button. In the dialog that opens you can choose between writing it to an iso-file or to burn it on an empty CD (if one is detected).

---

### Post by Slim Odds on 2009-09-16
> **3rdalbum said:**
> That will create a pure ISO9660 filesystem. If you wanted a different sort of filesystem, or if you wanted to create a video DVD filesystem, then consult the *genisoimage* man page.

In my opinion, the there is no way that you would want to use the ISO9660 for a linux system. It is much to restrictive and does not allow the types of filenames that linux uses.

UDF is more like it.

---

### Post by geirha on 2009-09-16
> **Slim Odds said:**
> In my opinion, the there is no way that you would want to use the ISO9660 for a linux system. It is much to restrictive and does not allow the types of filenames that linux uses.

UDF is more like it.

Usually you add the joliet and rockridge extensions for iso9660. With mkisofs/genisoimage, you do that with
```
genisoimage -J -r -o image-file.iso dir1/ dir2/ file1 ...
```

mkisofs and genisoimage is the same command btw. It used to be mkisofs, but has later changed name to genisoimage, so you should get used to using genisoimage rather than mkisofs, because the latter will eventually disappear.

---


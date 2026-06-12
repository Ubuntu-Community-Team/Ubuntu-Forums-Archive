---
title: "How do I re-format a &quot;1.44&quot; mb diskette (floppy)"
date: 2009-08-31
forum: General Help
---

### Post by jkb609gi8 on 2009-08-31
When I plugged in my Lacie external 1.44mb diskette driver into the laptop (with ubuntu 9.4 o/s), nothing happens. I cannot find the A/: Driver in the Home Folder (File Manager).

When I insert a diskette, an icon called MAIN FOLDER comes up on the Desktop, thus allowing me to view the contents. What I want to do is erase the contents or in other words re-format the diskette. I can not figure out how to format the diskette and write a new file onto it. :P

Then hope to burn a file called "grub-rescue-floppy.img" and see if I can boot my other laptop that has a corrupted grub. 

*******************************

(((( Want to learn more of my other problems? See regards to the last post, [ Error 18 on Post (And other issue) ] ...... Posted four or five days ago.

  	 	 	 	 	 	  When I enter on command line as follows;

Boot: sudo grub
 Could not find kernel image : sudo
 boot:

---

### Post by jkb609gi8 on 2009-08-31
P.S. I plugged the external floppy driver into the laptops USB port.

---

### Post by Soley on 2009-08-31
Well, with linux, you're not going to find a letter for a drive ever. So let's get that out of the way.

I haven't used a floppy in about 7 years meaning I haven't used one with linux. But I would imagine you would have to find where this floppy is being mounted. I think you can do this by typing, in a terminal:

```
sudo fdisk -l
```

Ignore any of the drives that have the name "sda" (/dev/sda*)

Look for another one with a very tiny file size (around 1440, I think)

Wherever it's being mounted, you're going to have to unmount it first. For this example I'm going to use FD for "floppy disk".

```
sudo umount /dev/fd
fdformat /dev/fd
```

If anyone can be more specific with using floppies with ubuntu, feel free. Hopefully this works for you.

---

### Post by alienclone on 2009-08-31
try a partition program like gparted or i read someone else solved their issue with gfloppy.

a link i found that may help you.

[http://ubuntuforums.org/showthread.php?t=824951](http://ubuntuforums.org/showthread.php?t=824951)

---


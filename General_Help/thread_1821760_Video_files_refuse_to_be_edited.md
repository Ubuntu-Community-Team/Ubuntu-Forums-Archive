---
title: "Video files refuse to be edited"
date: 2011-08-09
forum: General Help
---

### Post by davy jones on 2011-08-09
Two video files on my external hard disk refuse to be deleted, renamed or moved. They keep giving the following error message

Error removing file: No such file or directory
or
Error renaming file: Input/output error

Can someone please help me out??

---

### Post by HermanAB on 2011-08-09
If there are spaces or funny characters in the names, try putting quotes around the names.

---

### Post by cotcot on 2011-08-09
Can you load them in a video editor or can read the file properties ? (starting the video editor in terminal will maybe give you useful error messages)

---

### Post by davy jones on 2011-08-10
I tried putting quotes around the name of one because it had a strange character in it (which happened on its own) but that merely created a copy of the file right there with quotes around the name and now even that file refuses to be edited in any way.

I can view the files' properties and can open them in pitivi video editor too.

Still no luck

---

### Post by davy jones on 2011-08-10
I should mention that one of them is an incomplete mkv file. It refused to be fully copied onto the hard disk and only part of it got copied. But the other file is a complete avi file and it is totally unrelated to the first one.

---

### Post by HermanAB on 2011-08-10
OK, then you probably need to boot with a CDROM and run fsck, or configure the system to run fsck on next boot.

---

### Post by davy jones on 2011-08-10
Can you please tell me how to do that? I've never done it before. And I'm guessing my external hard disk needs to be connected at the time since that's where the files are?

---

### Post by cotcot on 2011-08-10
> **davy jones said:**
> I tried putting quotes around the name of one because it had a strange character in it (which happened on its own) but that merely created a copy of the file right there with quotes around the name and now even that file refuses to be edited in any way.

I can view the files' properties and can open them in pitivi video editor too.

Still no luck

If you can open them in pitivi maybe you can render it under a different name. You might loose some quality but at least you saved your file before doing other attempts to recover it.

---

### Post by davy jones on 2011-08-11
Ok so the problem is still not solved but when I mounted the disk on windows it refused to open the entire folder in which these two files are and gave an error message saying "file or directory is corrupt and unreadable". Formatting the disk again will work but I want to keep this as a last resort since it would mean backing up 400 gb of data. Please help

---

### Post by zero2xiii on 2011-08-11
It has happened to me before on a FAT32 formated thumb drive.

The only option, format. Nothing else works.

All I could find out that seemed to cause my problem, is the drive claimed to be 8GB while in effect it was only a 4GB, (Cheap MP3 Player.. heard they do this to make it seem "beter").. But as you exceed the actual disk space, data is written somewhere, but you cannot read it, or delete it or anything.

Good luck though. Might try the FSCK option. Maybe you are lucky.

Since its an external drive, try opening it up, connecting it directly to your pc, and check the smart status of the drive (Low level functions are lost due to the sata/ide to usb converters)

Again, good luck

EDIT:
Another question, how big is the files? And what is the farmating of the drive. I seem to recall you cant for example copy files larger than 2/4GB to a FAT32 formated drive.. Might also be a possible cause...

---

### Post by davy jones on 2011-08-11
My hard disk is a western digital and it has 1.4 TB of free space so I don't think that's the problem. And one file is just 700 mb or so, so size is not the issue.
Can you please tell me how exactly to run fcsk? I have never done it before so I don't know how. It will be extremely helpful if you could. Thanks.

---

### Post by davy jones on 2011-09-22
Ok I'm posting this on the same thread because its relevant. Very often I  get strange errors while transferring files onto my external hard disk  like "Error splicing file". And sometimes certain files and folders  refused to be deleted and they give errors like "Cannot delete  file/directory - Input/Output error". I tried to delete those  files/folders in windows but that didn't work either. I am really tired  of having to format the drive every time something like this happens.  I've done it thrice already and it takes ages to transfer all my data  back into it. So can someone PLEASE tell me a less weary solution to  this??

---

### Post by oldos2er on 2011-09-22
What filesystem is on the external disk?

---

### Post by davy jones on 2011-09-22
Ntfs

---

### Post by davy jones on 2011-09-22
So? Anything? I've tried to delete it via terminal using sudo rm as well as gksudo nautllus. It just doesn't work. I find it ridiculous that I have to format my hard disk every time this happens. It takes one whole day to transfer all my data back into it.

---

### Post by davy jones on 2011-09-23
Guys I seriously need some help here! Someone respond please!

---

### Post by oldos2er on 2011-09-23
I don't know much about NTFS, but have you run chkdsk on it?

---


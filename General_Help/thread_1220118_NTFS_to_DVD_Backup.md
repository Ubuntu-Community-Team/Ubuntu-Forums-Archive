---
title: "NTFS to DVD Backup"
date: 2009-07-22
forum: General Help
---

### Post by fjr0122 on 2009-07-22
Hello, 
I have a Hard Drive with an NTFS partition attached through USB. I need to backup that partition to a dvd, so that you can pop the dvd into a windows box and immediately read the files off of it. So no compressed files or wonky formatting. 

I've tried doing this kind of job before with windows and linux and there's always some files that are locked down by the old OS. So what I need is some utility or other way to strip the user permissions and other wierdness and copy every file from the hard drive to the dvd.

Any help with this backup would be really great, thanks.

---

### Post by NightwishFan on 2009-07-22
You could just burn a data dvd, and add windows compatibility. Brasero offers this option.

If you want to back up the NTFS drive as a NTFS image, I have no idea how. :D

---

### Post by cariboo on 2009-07-22
Depending on how much data you have on your ntfs partition, but you can use dd to create an iso of your data:

```
dd if=/dev/ntfspartition of=/somewhere/ntfs.iso
```

Change the paths to the ntfs partition and and storage path.

---

### Post by fjr0122 on 2009-07-22
It has about 8gb. 

Am I wrong or will that command make an iso no matter what size it is, just that I cant burn a 8gb ISO to a dvd. So it needs to be divided up somehow...

Would that be an exact image of the drive? I would like to strip the NTFS permissions so that any file on the drive can be viewed/run without worrying about permissions...

Any ideas?

---


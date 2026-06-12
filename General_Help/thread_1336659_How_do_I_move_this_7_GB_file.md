---
title: "How do I move this 7 GB file?"
date: 2009-11-24
forum: General Help
---

### Post by Zaytoven on 2009-11-24
I have a 16 GB flash drive. I need to move this 7 GB file onto my macbook witch uses +HFS. How do  I get this done? splitting it up into multiple rar files or what? If thats the way what is a good software that will do it for me? Whats a file system that mac and ubuntu can both read and write to so I can transfer this file.

---

### Post by falconindy on 2009-11-24
Is there a reason you can't use a network transfer?

---

### Post by HermanAB on 2009-11-24
Howdy,

Use 'split' to break the file into smaller pieces, then use 'cat' to glue it back together again:
$ split -b 2048M file.dat

$ cat file.dat0001>file.dat
$ cat file.dat0002>>file.dat
$ cat file.dat0003>>file.dat

The first time, use a single bracket, thereafter two brackets!

---

### Post by kircher on 2009-11-24
Ubuntu should have native support for HFS, and so you should be able to just move the 7GB file using your file manager (drag and drop or cut/copy and paste), or using
```
mv file location
```
where 'file' is the 7GB file, and 'location' is where you want to move it to.

Example:

I want to move a picture located in /media/cdrom/example.jpg to /home/horse I would use
```
mv /media/cdrom/example.jpg /home/horse
```

That is assuming I have access to these locations, otherwise I would need to use sudo

---

### Post by Zaytoven on 2009-11-24
when i try to place the file onto my +HFS formatted flash drive it says the directory is read only or something along those lines.

---

### Post by dcstar on 2009-11-24
> **Zaytoven said:**
> I have a 16 GB flash drive. I need to move this 7 GB file onto my macbook witch uses +HFS. How do  I get this done? splitting it up into multiple rar files or what? If thats the way what is a good software that will do it for me? Whats a file system that mac and ubuntu can both read and write to so I can transfer this file.

Format the USB to NTFS. No need to overcomplicate things.

---

### Post by kircher on 2009-11-24
> **Zaytoven said:**
> when i try to place the file onto my +HFS formatted flash drive it says the directory is read only or something along those lines.

Ok, it seems that write access to HFS+ is not enabled by default in Ubuntu. You could edit /etc/fstab, however I believe that is a clumsy way for a removable drive. Have a look here [http://www.ubuntuproductivity.com/journal/macintosh/08/2009/readwrite-to-hfs-on-ubuntu/](http://www.ubuntuproductivity.com/journal/macintosh/08/2009/readwrite-to-hfs-on-ubuntu/)

There may be a a way to set up write access for removable drives by default. For now you could try editing your /etc/fstab file. It's a shame that it doesn't work by default though.

---

### Post by kircher on 2009-11-24
as dcstar said, if it's possible to have the flash drive formatted with a new filesystem that can be shared across both systems, then that may be easier.

---


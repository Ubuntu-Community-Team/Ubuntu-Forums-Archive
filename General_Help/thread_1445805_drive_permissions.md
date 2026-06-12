---
title: "drive permissions"
date: 2010-04-03
forum: General Help
---

### Post by mike67114 on 2010-04-03
How do I change permissions for my USB thumb drive?

I have an 8-gig drive I'm using to assemble a photo gallery for my mother-in-law. Last night I went to make some adjustments and  was informed by a message box that I didn't have permissions to change anything on this read-only drive.

I'need an "educational moment" on how to change permissions on a drive and all the files on it.

Thanks!

---

### Post by chessnerd on 2010-04-03
To change permissions you use the chmod command.

Examples:

```
chmod 777 someFile.txt
```
Changes the permissions so that ANYONE can read, write, and execute the file.

```
chmod -R 755 someDirectory/
```
Recursively changes the permissions so that ANYONE can read and execute every file in the directory and every file in every directory below that directory. However, only the owner of the files can write to them. This is probably what you are looking for, and the directory for the flashdrive should be found in /media

An explanation of the numbers can be found here: [http://www.pageresource.com/cgirec/chmod.htm](http://www.pageresource.com/cgirec/chmod.htm)

Good luck.

---


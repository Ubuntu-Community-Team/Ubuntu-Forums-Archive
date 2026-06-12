---
title: "Whoops, deleted a partition, need my files"
date: 2011-03-05
forum: General Help
---

### Post by Mister Fowler on 2011-03-05
Hello, I was installing windows (don't ask) and had my external HD plugged in and accidentally deleted its partition. I have Ubuntu back and am wondering what I can use to get into the disk and retrieve my files.

Once again, the files are on an external HD, and the partition information is now gone. I hope the community can help me.

---

### Post by turtle153 on 2011-03-05
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery) but it sounds like you might be too late :(

---

### Post by Mister Fowler on 2011-03-05
Thank you for the quick replay. I am trying the recovery, but when trying sudo parted /dev/sdb I get:

"invalid token: sudo"

---

### Post by sesipdo on 2011-03-05
u can get ur files back .. do u have another computer that u can use to burn a cd ? 


and have u reinstalled your os ?
and yes there is a windows program that will go back and look at all your files.
I dont know that it would go into a Linux partition ... u could give it a shot and it is not free but u can go and download it from like PB or some thing like that if you wanted to .... :P 

let me know if you would like that program name ....

---

### Post by Mister Fowler on 2011-03-05
I am on Ubuntu, the drive I am referring to is external, a backup drive for data I messed up.

---

### Post by sesipdo on 2011-03-05
o okay well in that case do u have a windows machine ?

or only a Ubuntu ?

---

### Post by Mister Fowler on 2011-03-05
I have a windows machine, yes.

---

### Post by sesipdo on 2011-03-05
okay

are u conferable with downloading onto the windows... like with a torrent?

and u can use the windows to try and get files back with a program that i use to use but it cost money.. but if you dont want to pay for a one time use that it may not work then u cna get the software for free buy download and that is up to you ..

the software is called ```
easeus-hard drive data recovery
```

---

### Post by alphaamanitin on 2011-03-05
When I deleted and reformatted a drive I was able to recover it 100% by cloning the drive with dd, placing the clone in the new computer and using TestDisk, works on Linux and Windows (I used Windows 7).  After reinstalling the windows XP boot loader using SuperGrub I had my computer back 100%, as if nothing happened.  PM me if you want more info.

AlphaA

---

### Post by clhsharky on 2011-03-05
Mister Fowler


If you dont mind command line, "ext undelete" is fast, good for large drives, and not as hard as one might think.
[http://extundelete.sourceforge.net/](http://extundelete.sourceforge.net/)


Sharky

---

### Post by Primefalcon on 2011-03-05
run testdisk from a buntu live cd/usb and you should be able to recover the whole partition

---


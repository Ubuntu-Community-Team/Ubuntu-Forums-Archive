---
title: "Access files in ubuntu 9.10 from windows 7"
date: 2009-12-03
forum: General Help
---

### Post by joy83 on 2009-12-03
I was wondering if there is any way to access files that I have in Ubuntu when I am in Windows 7.  My computer is dual booted with both Windows 7 and Ubuntu 9.10. I have tried some known programs like f-disk and another one whose name I cannot remember but none of them are compatible with Win 7.

Any suggestions?

---

### Post by Some Penguin on 2009-12-03
Depends on the filesystem.  This is a filesystem issue, not an Ubuntu issue, technically.

[http://www.networkedmediatank.com/showthread.php?tid=23220](http://www.networkedmediatank.com/showthread.php?tid=23220)

might be useful for ext2/ext3 fs, for instance.

and [http://ubuntuforums.org/showthread.php?t=1145598 ]("http://ubuntuforums.org/showthread.php?t=1145598")

for ext4.

---

### Post by Fire_Chief on 2009-12-03
***If*** you installed Ubuntu with the ext3 filesystem instead of ext4, you could use the Windows FS driver for ext2 [http://www.fs-driver.org/]("http://www.fs-driver.org/")(compatible w/ ext3) or if you just want to read the files, you could also try linux-reader [http://www.diskinternals.com/linux-reader/]("http://www.diskinternals.com/linux-reader/")

I've used the FS driver in Windows 7 with no problems. Have not tried it with ext4.

Cheers!

---

### Post by zeplin1947 on 2009-12-03
[SIZE=4]If you click on "Places" to bring up a drop down menu of folders on hard drive , one will be the file system on windows 7, I'm using Vista and it says, 98 GB Filesystem which the size of the windows partition, if you click on it then it asks for your password and you will have access to files listed under C:\[/SIZE]

---

### Post by rmockler on 2009-12-03
This link is to a program that I downloaded and installed first in Vista, and then in Windows 7 and it worked perfectly for me.  I can find and open all my files in Ubuntu with it right from Windows 7.

[http://sourceforge.net/projects/ext2fsd/files/](http://sourceforge.net/projects/ext2fsd/files/)

---

### Post by joy83 on 2009-12-03
> **rmockler said:**
> This link is to a program that I downloaded and installed first in Vista, and then in Windows 7 and it worked perfectly for me.  I can find and open all my files in Ubuntu with it right from Windows 7.

[http://sourceforge.net/projects/ext2fsd/files/](http://sourceforge.net/projects/ext2fsd/files/)

So I downloaded this and installed it in Win 7. It seems to show my ubuntu partition but how do I now see the files there?

---

### Post by rmockler on 2009-12-03
How I do it, is when I click on My Computer, it shows the C: drive for Windows and the L: drive (I named it that) for Ubuntu.  If I double click on the L: drive it opens it showing a bunch of folders.  I then open the home folder and my personal folders are in there.

---


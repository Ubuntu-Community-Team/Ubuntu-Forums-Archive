---
title: "When I installed Ubuntu it spilt my HD up with Windows 7"
date: 2010-05-12
forum: General Help
---

### Post by darkfloor on 2010-05-12
I'm new to Linux and not sure I've done this right.

When I installed Ubuntu 10.04 it gave me a few options and I decided to partition my HD (a 1TB) into 2, one for the existing Windows 7 install and one for Ubuntu.

When in Ubuntu I can access the Windows 7 partition, but I can't seem to find/access the Ubuntu drive when I'm in Windows.

How can I set up that drive/partition so that I can view/edit it in Windows.

---

### Post by ronnielsen1 on 2010-05-12
You need a 3rd party program 

[http://www.howtoforge.com/access-linux-partitions-from-windows](http://www.howtoforge.com/access-linux-partitions-from-windows)

---

### Post by Vaphell on 2010-05-12
you know, it comes to microsoft making life of the infidels hard. They didn't bother to provide compatibility with non-windows filesystems so your win7 doesn't know what to do with your ext3/ext4 partition. Ubuntu has ability to read fat/ntfs so you can access windows data just fine.
You'd need some ext2/3/4 driver for windows, i've seen and used one, but i don't know if it fully supports win7 and ext3/4 filesystems. I guess Google has the answers.

---

### Post by darkfloor on 2010-05-12
> **ronnielsen1 said:**
> You need a 3rd party program 

[http://www.howtoforge.com/access-linux-partitions-from-windows](http://www.howtoforge.com/access-linux-partitions-from-windows)
Nice, I tried the 3rd option as it allowed read/write access and it doesn't work with Windows 7.


Will keep looking. Thank you for the post thou. :)

---

### Post by ronnielsen1 on 2010-05-12
I believe it does work in Windows 7 if you install in XP Compatability mode

---

### Post by ronnielsen1 on 2010-05-12
This site says vista mode

[QUOTE]
- To install Ext2IFS you have to run the installer under compatability mode choosing Windows Vista, not Windows XP because this will not work.
- After installation you will be able to assign a drive letter to your drive and be able to acces it./[QUOTE]

[http://www.networkedmediatank.com/showthread.php?tid=23220](http://www.networkedmediatank.com/showthread.php?tid=23220)

There's also this you could try

[http://sourceforge.net/projects/ext2fsd/files/](http://sourceforge.net/projects/ext2fsd/files/)

---

### Post by ajgreeny on 2010-05-12
Last time I tried this, I could not find anything that would work with ext4 file systems.  No problem with ext3, but if you installed ubuntu as the default ext4, you may be unlucky, unless the drivers used in windows have now been updated.

---

### Post by Objekt on 2010-05-12
There are a couple of installable file systems out there, that is, utilities that allow Windows to read non-Microsoft file systems such as ext2/3/4.

One is simply called "Ext2 Installable File System For Windows" ([http://www.fs-driver.org/](http://www.fs-driver.org/)).  Although called "Ext2," it is supposed to work with ext3 and ext4 as well.  It's never worked for me in Windows XP, but supposedly works in Vista, and so ought to work in 7 as well.

Another is ext2fsd.  Homepage: [http://www.ext2fsd.com/]("http://www.ext2fsd.com/")  I had better luck with this one.  Again, although ext2 is in the name, it works with ext3.  Not sure whether it handles ext4, as I don't have any ext4 volumes.

One of those should do what you need.  There may be other installable file systems as well.

---


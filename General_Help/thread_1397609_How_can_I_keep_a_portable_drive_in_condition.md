---
title: "How can I keep a portable drive in condition"
date: 2010-02-03
forum: General Help
---

### Post by codger76028 on 2010-02-03
Probably a dumb beginner question, but here it is.  I know that one does not need to defrag in Linux  However, what about when using fat32 portable hard drives?  I have one that is primarily connected to my Linux box, but I want it to be available to transfer to my wife's Window's box.  I add and delete files from it every day.  Does it need to be defragged?  If so, do I need to connect it to my wife's box from time to time to do that?

---

### Post by mörgæs on 2010-02-04
I wouldn't bother with that, as it is only used for storage. The main hard drive on a system contains the programs themselves (Open Office, Gimp, ...), which gives a lot more disk activity. 

About fragmenting in general:
[http://www.whylinuxisbetter.net/items/defragment/](http://www.whylinuxisbetter.net/items/defragment/)
[http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting](http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting)

---

### Post by codger76028 on 2010-02-09
Thanks.  I guess my question has to do with whether the os (Linux, Windows) controls fragmentation or whether the filesystem (ext4, fat32) does.  If it is the os, then no problem.  If it is the filesystem, then the fat32 external drive will need defragging even if used exclusively under Linux.

---

### Post by jamesisin on 2010-02-09
When you save a new file to a filesystem, your operating system will seek out a contiguous space in which to save that file.

Since you are talking about adding and removing files can we assume that you will *not* be keeping the drive near full?  Fragmentation should only be a problem as you fill the drive (and contiguous spaces become scarcer).

Further, there is little point in worrying about fragmentation if you intend to pull the files off the drive anyway.  Fragmentation will only have an impact if you are attempting to *use* the fragmented files.

(One method of defragmentation is moving the files off a drive and back onto that drive as this gives the OS the opportunity to re-allocate contiguous spaces.)

---

### Post by codger76028 on 2010-02-16
That makes sense.  Many thanks

---

### Post by jamesisin on 2010-02-17
Glad to be of service.

You may want to mark your thread as SOLVED in Thread Tools above.

---

### Post by pSYcl0Ne on 2010-02-17
what tool/program is there for defragmenting in ubuntu? and will having ntfsprogs mean this tool (if there is one) can also defragment a windows partition?

---

### Post by audiomick on 2010-02-17
Hallo.
If your are still here, you might want to have a read of this
[http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting](http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting)
I gives a rather good explanation of why fragmenting occurs and why some file system are prone to it and not others.

In answer to your question; fragmentation is a function of the file system, not the OS.

---

### Post by jamesisin on 2010-02-17
> **pSYcl0Ne said:**
> what tool/program is there for defragmenting in ubuntu? and will having ntfsprogs mean this tool (if there is one) can also defragment a windows partition?

There is some debate on the matter, but as a general rule if you keep your Ubuntu system at, say, <80% hard drive capacity you should not need to defragment your drives.

You can find several threads here on the forums with discussions about fragmentation and tools which may or may not suit your needs.

---


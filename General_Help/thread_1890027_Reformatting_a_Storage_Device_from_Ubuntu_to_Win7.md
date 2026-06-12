---
title: "Reformatting a Storage Device from Ubuntu to Win7"
date: 2011-12-02
forum: General Help
---

### Post by notoriousmic24 on 2011-12-02
Hello all, and thanks in advance...

I used an old laptop hard drive as an exteranal for quite sometime, and never had a problem accessing it with my Ubuntu machine. Overtime, I noticed that I could not access it via any Windows machine (XP, Vista, Win7). Currently I need to access it on a Windows 7 machine. It recognizes it on "devices and Printers", but I can't access any files and it does not appear on Hard Disk Drives. If I plug it back in to my Ubuntu machine it works fine. It's a Serial-ATA bridge if that helps.

My question is:

-how can I manage to get it to work on the Windows machine? 

OR

-how can I reformat it on my Ubuntu machine so that I can use it on my Windows machine? ( I don't mind a wipe of files)

---

### Post by batharoy on 2011-12-02
You can use Disk Utility to format it as either FAT or NTFS, windows will recognize both.

---

### Post by staf0048 on 2011-12-02
I realize I might be a little late, but instead of wiping the drive completely, you could just install an ext(x) file system reader on Windows.  See here:  [http://www.ubuntugeek.com/how-to-read-ext3ext4-linux-partition-from-windows-7.html](http://www.ubuntugeek.com/how-to-read-ext3ext4-linux-partition-from-windows-7.html)

The problem is that Windows comes with only support for their file system, so you need to add support on your own to read other types.

Best wishes,

---

### Post by notoriousmic24 on 2011-12-05
> **staf0048 said:**
> I realize I might be a little late, but instead of wiping the drive completely, you could just install an ext(x) file system reader on Windows.  See here:  [http://www.ubuntugeek.com/how-to-read-ext3ext4-linux-partition-from-windows-7.html](http://www.ubuntugeek.com/how-to-read-ext3ext4-linux-partition-from-windows-7.html)

The problem is that Windows comes with only support for their file system, so you need to add support on your own to read other types.

Best wishes,

You're not late at all. Thanks for the help, I will check it out

---

### Post by notoriousmic24 on 2011-12-05
It worked! I still had to format it, but I was able to save everything before. Thanks staf0048

---


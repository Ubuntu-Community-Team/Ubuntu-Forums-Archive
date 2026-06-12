---
title: "palimpsest, ntfs partition attribute modification"
date: 2010-03-20
forum: General Help
---

### Post by faridux31 on 2010-03-20
Hello,
This is my first post in english, I hope I won't do too many mistakes!!
Well, I have migrated from Micro$oft to Ubuntu 9.1 last week,
I have to say this release is really amazing!!

Here is my concern:
In Windows, I had 2 partitions C:\ and D:\, now they appear as /dev/sda1 and /dev/sda31
I have installed ubuntu OS on /dev/sda1, and I have mounted /dev/sda3 in the /etc/fstab file, everything works fine.
I would like to upgrade the filesystem /dev/sda3 from NTFS to Linux FS (0x83) in palimpsest, but this partion contains around 100Gb of data I do not want to loose.
Here is my question:
In palimpsest, if we modify the type of a partion and click apply, does this format the filesystem or is it just an upgrade without any dataloss
Thank you for your help

---

### Post by DawieS on 2010-03-20
Welcome to the Ubuntu Forums!:grin:

I recommend that you install **gparted** with **Synaptic Package Manager**. With **gparted** you can resize or move partitions, and format them to the required type of file-system. Be sure to always back-up your important data. Search for advice on how to use **gparted**, there are lots of threads in the forums on the subject, for example [_**this**_]("http://ubuntuforums.org/showthread.php?t=1429460") thread.
:grin:

---

### Post by Morbius1 on 2010-03-20
You can't convert an ntfs partition to an ext3/4 partition without a format, in which case you will loose all your data.

You don't really need to convert the ntfs partition you know. It's a legitimate filysystem in it's own right and a lot of good people from Digital Equipment Corporation worked very hard to make it possible ;)

Linux can read and write to an NTFS partiton.

I would agree with DawieS on using gparted. Maybe it's because it's what I've always used but **palimpsest **just makes me uncomfortable[B]. ;)
[/B]

---

### Post by faridux31 on 2010-03-21
Hi,

Thank you, I will have a look to gparted

Cheers!

---


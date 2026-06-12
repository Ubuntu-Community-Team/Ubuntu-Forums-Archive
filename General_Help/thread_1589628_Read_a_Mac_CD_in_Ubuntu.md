---
title: "Read a Mac CD in Ubuntu"
date: 2010-10-06
forum: General Help
---

### Post by Hickory420 on 2010-10-06
Hi Guys,

I have searched Google and throughout these forums, but I can not find any information on how to read a CD, burned by a Mac, on my Ubuntu machine. Is there any way possible to do this? I'm sure there would have to be a way because, well, Mac and Ubuntu have their similarities...

Thank you in advance! 

Hickory :guitar:

---

### Post by Quackers on 2010-10-06
What kind of files are on the cd. Have you tried reading any other cd's on the same drive?

---

### Post by Hickory420 on 2010-10-06
Apparently the files on the CD are image files... The cd drive works as I use it quite frequently. 
Ubuntu does not recognise the fact that I have inserted a cd. Browsing the /media/cdrom and /media/cdrom0 prove to be unsuccessful...

And thanks for the quick reply ;)

---

### Post by srs5694 on 2010-10-06
Try the following commands:

```

sudo mkdir /media/test
sudo mount -t iso9660 /dev/dvd /media/test
ls /media/test
sudo mount -t udf /dev/dvd /media/test
ls /media/test
sudo mount -t hfs /dev/dvd /media/test
ls /media/test
sudo mount -t hfsplus /dev/dvd /media/test

```

Change "/dev/dvd" to "/dev/cdrom", "/dev/sr0", or whatever device file is appropriate on your system, if necessary. Stop after the ls command shows files in /media/test. If those files aren't the ones you expect, type "sudo umount /media/test" and continue with the list. Basically, the idea is to force the system to try each of the filesystems that might plausibly be on the disc -- iso9660, udf, hfs, and hfsplus. Some discs have multiple formats. Sometimes the same files are accessible in all the formats, but other times you'll see just a subset of files, or a file containing a note that you need to use the disc on a particular OS, if you mount it with the wrong filesystem type.

---

### Post by Hickory420 on 2010-10-06
> **srs5694 said:**
> Try the following commands:

```

sudo mkdir /media/test
sudo mount -t iso9660 /dev/dvd /media/test
ls /media/test
sudo mount -t udf /dev/dvd /media/test
ls /media/test
sudo mount -t hfs /dev/dvd /media/test
ls /media/test
sudo mount -t hfsplus /dev/dvd /media/test

```


CHAMPION!!!!!

```

sudo mount -t hfsplus /dev/cdrom /media/test

```

That was the line that worked for me :)
:guitar:
):P
\\:D/
=D>
:biggrin:
:KS
:lolflag:
Well, this is now solved. Thank you very much.

---

### Post by srs5694 on 2010-10-06
Glad to have helped. If you need to mount this CD/DVD, or others like it, regularly, you can add an /etc/fstab entry for it:

```

/dev/dvd  /mnt/maccd  hfsplus  users,noauto  0  0

```

Create the /mnt/maccd directory and then type "mount /mnt/maccd" to mount it. (You can do this as an ordinary user with the preceding /etc/fstab entry.) When you're done, type "umount /mnt/maccd".

---

### Post by Hickory420 on 2010-10-06
> **srs5694 said:**
> Glad to have helped. If you need to mount this CD/DVD, or others like it, regularly, you can add an /etc/fstab entry for it:

```

/dev/dvd  /mnt/maccd  hfsplus  users,noauto  0  0

```

Create the /mnt/maccd directory and then type "mount /mnt/maccd" to mount it. (You can do this as an ordinary user with the preceding /etc/fstab entry.) When you're done, type "umount /mnt/maccd".



Done and Done! Very cool. This is a massive time saver :) Absolute legend!

---

### Post by Quackers on 2010-10-06
Hickory420, if you are satisfied that your questions are answered can you please mark the thread as solved as it may help others. If you look near the top in red click on Thread Tools and select mark as solved. Thanks :-)

---

### Post by Hickory420 on 2010-10-06
> **Quackers said:**
> Hickory420, if you are satisfied that your questions are answered can you please mark the thread as solved as it may help others. If you look near the top in red click on Thread Tools and select mark as solved. Thanks :-)

Done deal ;)

---


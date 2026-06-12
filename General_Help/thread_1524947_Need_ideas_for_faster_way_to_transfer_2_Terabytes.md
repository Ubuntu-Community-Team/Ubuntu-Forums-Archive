---
title: "Need ideas for faster way to transfer 2 Terabytes"
date: 2010-07-06
forum: General Help
---

### Post by jeeves on 2010-07-06
I need to find a fast way to copy a folder containing about 2 terabytes over my home network to another Ubuntu machine.

In the past I  have used RSYNC over ssh, but this is far too slow for this much data (probably the ssh encryption overhead slowing things down)


**Any  ideas for accomplishing this.**

I  have looked at using SAMBA, but this seems geared for a mixed Linux/Windows network. Also I don't know if SAMBA will be appreciably faster.

---

### Post by GreenN00b on 2010-07-06
Before you start looking you may start copying the data, it may be finished by the time you find a faster way ;).

One of my friends has looked for a week for something like this - at a speed of 4 MB/second it should be over in less than a week ...

---

### Post by CannibalZerg on 2010-07-06
FTP is pretty fast, much faster than SSH and Samba,  you can use one of lightweight ftp server: vsftpd; proftpd; etc.

---

### Post by marshmallow1304 on 2010-07-06
From what I've read, FTP and NFS have similar performance (certainly much faster than sshfs), so go with whichever one is easier to set up.

---

### Post by nirvana8510 on 2010-07-06
I have two ideas for you, just choose one, software or hardware.

For software, you can use the softwares stated above or just create an FTP server for direct transfer.

For me, if you're gonna transfer a staggering 2TB of data, i would prefer you to use an HDD Enclosure.

Just remove your hard disk drive temporarily, connect it into a so called "HDD enclosure".

HDD enclosure is just like a usb devise but in this case, it has its own power supply connected into a plug, then a USB2.0 port.

And then, that's it, you've just made a hard disk like a usb, though it's not as portable as i think, but it would help you bring that much of data anywhere you go. :D

---


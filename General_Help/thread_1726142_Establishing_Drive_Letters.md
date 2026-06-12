---
title: "Establishing Drive Letters"
date: 2011-04-10
forum: General Help
---

### Post by Ted3929 on 2011-04-10
I'm using ArtistX 1.0 and had modified it to the point I'd like to create a persistent USB drive so I can computer hop while also saving changes.

Problem is, my program, Universal USB Installer (pendrivelinux.com) works in Wine up to a point (it's really a Windows program but I'm not using Windows any more).

The program works up to the point I"ve got to establish a designation drive, i.e. the USB flash drive I want to use.  At that point it stalls because the program uses drive letters ala Windows and doesn't recognize drive names like Ubuntu utilizes (instead of drive E, Ubuntu shows 2.0 GB Filesystem.

Is there any way of establishing a drive letter system in Ubuntu for flash drives or does it go strictly by name?

Thanks

---

### Post by WorMzy on 2011-04-10
It's not possible, afaik.

All absolute paths start with "/", the backslash that Windows paths use requires escaping, and all folders on UNIX and UNIX-like OSs use a forward slash. So "C:\" would have to be "/C:\\/", which doesn't really work.

Although, saying that, I think Wine implements it's own pseudo-filesystem, where "Z:\" is actually ~/.wine/drive_c/, or whatever, so maybe you could sort something out with symlinks and wineconfig.

---

### Post by Ted3929 on 2011-04-10
I was afraid of that.  Guess I was hoping for some back door method of cheating the system but it's not to be.

Thanks Anyway!

---


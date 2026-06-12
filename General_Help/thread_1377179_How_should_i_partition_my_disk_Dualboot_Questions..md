---
title: "How should i partition my disk? Dualboot Questions."
date: 2010-01-10
forum: General Help
---

### Post by jakeeee on 2010-01-10
Alrighht.
Im about to dual boot Ubuntu 9.10 and windows 7.
Im currently using Karmic.

How should i go about partitioning my 150gb disk?
Im installing windows 1st. then ubuntu. seems easier..

Ive never done a dualboot before.

I have a couple questions about it.

Should I make a seperate partition for all my music?
I would want to play it both on Ubuntu and Windows....

How much space for each patition?

Can i acsess my files on both operating systems?

Thanks for your time and replys in advance :P

---

### Post by Sef on 2010-01-10
> How should i go about partitioning my 150gb disk?
Im installing windows 1st. then ubuntu. seems easier..

That is correct.  Install Windows first on the first primary partition.

> Should I make a seperate partition for all my music?
I would want to play it both on Ubuntu and Windows....es

Yes, make a separate home partition.

 > How much space for each patition?

Windows 20 GB; Ubuntu 10 GB; swap 1 gb; home partition the rest.

Windows needs to be NTFS;  Ubuntu can be ext4 - the default file system in Karmic.;  Swap needs to be swap; the home partition should be NTFS.    (You will need to install NTFS Configuration Tool, so Ubuntu can read and write to it.)


 > Can i acsess my files on both operating systems?


Make your home partition file system NTFS.

---

### Post by Jackzor on 2010-01-10
[http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony](http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony)

---

### Post by lukeiamyourfather on 2010-01-10
> **Sef said:**
> That is correct.  Install Windows first on the first primary partition.

es

Yes, make a separate home partition.

 

Windows 20 GB; Ubuntu 10 GB; swap 1 gb; home partition the rest.

Windows needs to be NTFS;  Ubuntu can be ext4 - the default file system in Karmic.;  Swap needs to be swap; the home partition should be NTFS.    (You will need to install NTFS Configuration Tool, so Ubuntu can read and write to it.)
 

Make your home partition file system NTFS.

I'd make the /home partition ext3 since there's installable file systems to read it in Windows. Using NTFS as a native file system in Linux for any partition is not a good idea. Note ext4 is not mountable in Windows at all (installable file system or not). Cheers!

---

### Post by jakeeee on 2010-01-10
Thanks for all your replys again :D
Really helped :)

---

### Post by michy99 on 2010-01-10
Just to be clear, /home can NOT be nfts. It needs to support linux permissions. The better idea is to create a separate ntfs partition for data which is shared between Windows and Ubuntu.

---


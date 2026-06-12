---
title: "Tar command and tape drives"
date: 2010-03-08
forum: General Help
---

### Post by e24ohm on 2010-03-08
Folks:
I am looking at getting a DLT drive for my network; however, I have never used the tar command with a tape drive.

What happens if the data is larger then 1 tape? Does the tar application automatically span tapes or do I need to use switches so it spans multipule tapes?

Right now my Full backup will take 2 or 3 tapes.

thanks.
J

---

### Post by TeoBigusGeekus on 2010-03-08
Correct me if I'm wrong but I don't think that the tar format supports volume split. Try rar instead.

---

### Post by Villiam on 2010-03-08
The method tar uses to detect end of tape is not perfect, and fails on some operating systems or on some devices.  If tar cannot detect the end of the tape itself, you can use &#8216;--tape-length&#8217; option to inform it about the capacity of the tape. Its from a weblink: [http://www.gnu.org/software/automake/manual/tar/Multi_002dVolume-Archives.html](http://www.gnu.org/software/automake/manual/tar/Multi_002dVolume-Archives.html)

---

### Post by e24ohm on 2010-03-08
> **Villiam said:**
> The method tar uses to detect end of tape is not perfect, and fails on some operating systems or on some devices.  If tar cannot detect the end of the tape itself, you can use ‘--tape-length’ option to inform it about the capacity of the tape. Its from a weblink: [http://www.gnu.org/software/automake/manual/tar/Multi_002dVolume-Archives.html](http://www.gnu.org/software/automake/manual/tar/Multi_002dVolume-Archives.html)
rocks mate...thanks!!!

cheers

---


---
title: "Software Sources problem.."
date: 2010-11-06
forum: General Help
---

### Post by MrSpencr on 2010-11-06
I am trying to download Wine and according to their directions I need to open System > Administration > Software Sources.

Problem is that it's not there:
[IMG]http://i620.photobucket.com/albums/tt284/Sp3ncerPix/softysources.png[/IMG]

But I know it is somewhere on my computer because:
[IMG]http://i620.photobucket.com/albums/tt284/Sp3ncerPix/itstheree.png[/IMG]

btw: this is my first day using Linux.

---

### Post by Foxheadz on 2010-11-06
alt+f2 Software sources might work, but if you just want to install it you can search for it in the software center

---

### Post by MrSpencr on 2010-11-06
> **Foxheadz said:**
> alt+f2 Software sources might work, but if you just want to install it you can search for it in the software center

According to software center it already is installed.

bump.

---

### Post by Foxheadz on 2010-11-06
I mean wine you can install wine from the software center and also you  can edit the software sources threw the software center by ubuntu software center>edit > software sources

---

### Post by MrSpencr on 2010-11-07
Ok. I now have wine DL'd via terminal AND software sources and I still get this error message when I try to open .exe files.

```
Archive:  /home/spencer/Downloads/CORE10k.EXE
[/home/spencer/Downloads/CORE10k.EXE]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
zipinfo:  cannot find zipfile directory in one of /home/spencer/Downloads/CORE10k.EXE or
          /home/spencer/Downloads/CORE10k.EXE.zip, and cannot find /home/spencer/Downloads/CORE10k.EXE.ZIP, period.

```

?

---

### Post by Foxheadz on 2010-11-07
Ok This part is sort of complicated to explain so ill make it as simple as i can.
1. Right click on the file and select properties
2. Go to the permission tab at the top, and under permissions set it to executable.
3. Quit the properties window.
4. Right click on the file again and this time click open with wine

---


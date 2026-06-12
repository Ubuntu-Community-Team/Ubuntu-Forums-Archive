---
title: "Cannot extract .iso (win7 language pack)"
date: 2009-10-02
forum: General Help
---

### Post by mogliii on 2009-10-02
Hi,

I have an .iso file (mu_windows_7_language_pack_x64_dvd_x15-73276.iso). When I say "Extract here" it extracts an 135 bytes large README.TXT
```
This disc contains a "UDF" file system and requires an operating system

that supports the ISO-13346 "UDF" file system specification.

```

Does Linux not support this? I understand it is for Windows, but... well... I got used to open anything in Linux.

Some more info:
```
file *.iso
mu_windows_7_language_pack_x64_dvd_x15-73276.iso: UDF filesystem data (version 1.5) 'GRMCXLP1_DVD

md5sum *.iso
4fd12ad4c946dd145a67c3230650ab8b  mu_windows_7_language_pack_x64_dvd_x15-73276.iso
```

---

### Post by Mercury_Alpha on 2009-10-02
Just search for "UDF" in Synaptic and you'll find a few packages you can install to add UDF support. I believe the main one is "libudf0."

---

### Post by user333 on 2009-10-02
I would try installing 7ZIP GUI under WINE.

[http://www.7-zip.org/](http://www.7-zip.org/)

This might work. Another way would be too install a open source Windows iso burning software, like burning mill express, burn the dvd, and then copy the contents into your hard drive. Of cource this isn't the best way to do it. Do this if you can't do it any other way.

[http://www.burningmill.com/](http://www.burningmill.com/)

I have never tried doing something like this on Ubuntu, but I have with 7z under XP. I think that using wine would be the key, because it should make up for Windows related problems, but some times it doesn't support everything.

I hope this helps! I never really dealt with this in Linux, so I might be wrong.:D

---

### Post by mogliii on 2009-10-03
Hi,

I could extract it in Windows with WinRAR. But actually that Win7 Language pack is a bu**sh**.

For Home and Professional you have to decide beforehand which language you want to install and make a new install medium. Only the versions above allow multiple languages. Ubuntu, by the way, has no problem with that.

I don't want to complain too much as I got Win7 from MSDN-Academy for free, but... wtf? It's year 2009 in a highly globalized/mobile society and I cannot change the language of my Win7 pro without reinstalling?

Anyway, thank you for your help.

---

### Post by mistermartin75 on 2010-04-06
If you install 7zip from the Ubuntu Software Center, you can extract UDF ISO images. I've just succesfully extracted the Windows 7 Professional ISO.

---


---
title: "AudioTester, Installing source code"
date: 2011-05-23
forum: General Help
---

### Post by oaxacamatt1 on 2011-05-23
Hi all,
I am having a problem installing a program, **AudioTester v1.6** and tests FLACs for errors.
[http://www.vuplayer.com/other.php](http://www.vuplayer.com/other.php)

The .zip file has a windows executable '.exe' and the source code. The code was written for Windows. The source code is written in C++ (.cpp) with C header (.h) files, xml (.vcproj) and one '.exe.manifest'(?) file. 

I tried the usual commands for compiling (./configure, autogen, make) the source code but no luck. 

Can I compile this code for Ubuntu/linux? Is there anything I can do with the code? And If so what do I need to do.
Any help would be appreciated,
M

---

### Post by TeoBigusGeekus on 2011-05-23
You can't expect source code for windows to compile in linux.
What you need to do, is (gulp...) read the whole source code, replace the windows libraries and their functions with linux ones, if they exist at all...
If not, you'll have to write them yourself!!!
May the force be with you - it's a tremendous task...

---

### Post by oaxacamatt1 on 2011-05-23
Hi Teo,
Thanks for the info. Now I know.  I guess I will put that one to bed.
Cheers,
M

---

### Post by mc4man on 2011-05-23
You could likely run it thru wine - though you can test flac files with flac
(flac --help

---

### Post by oldos2er on 2011-05-23
```
flac -t *.flac
``` will test flac files for errors.

---

### Post by oaxacamatt1 on 2011-05-23
Hi all,
I did try the program thru Wine and it works, but now that 'Old0S2er' mentioned the FLAC  command that sound 'Very nice'.
Cheers all for your answers,
M

PS. OldOS2er does that mean you used OS2 or you wrote it?  ;D  Cuz I remember using OS2 in the early 90's, Just like windows 3.11.

---

### Post by oldos2er on 2011-05-24
Just an OS/2 user....

---


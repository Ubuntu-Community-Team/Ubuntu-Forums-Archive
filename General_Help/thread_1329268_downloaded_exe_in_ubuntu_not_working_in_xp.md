---
title: "downloaded exe in ubuntu not working in xp"
date: 2009-11-17
forum: General Help
---

### Post by chandubaba on 2009-11-17
I have ubuntu and xp dual boot.
I downloaded flstudio 9 in ubuntu using a download accelerator.( cause internet in ubuntu is faster). But now that exe file is showing error in xp saying nsis error
[http://nsis.sourceforge.net/Why_do_I_get_NSIS_Error](http://nsis.sourceforge.net/Why_do_I_get_NSIS_Error)

may be(not sure) because ubuntu is ext3 and xp is ntfs :(
how to solve this problem!!

I cant download again (it takes 3 hours).

Sorry i marked it as kubuntu.. its actually ubuntu (new here)

---

### Post by coffeecat on 2009-11-17
> **chandubaba said:**
> may be(not sure) because ubuntu is ext3 and xp is ntfs

If you mean that you downloaded the *.exe file onto your ext3 partition, copied it to the NTFS partition and now you get the error when you try to run it in Windows - no. The fact that the file was on an ext3 partition will not affect it. I have downloaded Windows installers while in Ubuntu, transferred them to my C: partition and then installed them many times without problem.

The most likely explanation is that the file was corrupted in download. This happens occasionally. It's why you are advised to do a md5sum check on Linux ISOs before burning them to disc. I should imagine the "self-check" mentioned in that link is something similar - some sort of hash check.

Sorry - it looks as though you may have to re-download.

By the way, your link advises not using a download accelerator. That may be the problem.

---

### Post by Giblet5 on 2009-11-17
+1 on the corrupted download.

It either transferred incorrectly (not likely) or it is corrupted on the server from which you downloaded it.

If you downloaded the .exe to a flash drive, then pulled the flash drive out w/o unmounting it, that will do it too (on Ubuntu, on Windows, on Mac, on anything).

---

### Post by Aubergines on 2009-11-17
Don't think you can do much about it. You get the error because the file you downloaded is corrupted. You'll probably need to redownload it, there might be tools to fix it like [frlx](http://www.r1ch.net/projects/fr1x/) but it's pretty out of date, there might be others around - no idea if they work. Doesn't look good, sorry.

---


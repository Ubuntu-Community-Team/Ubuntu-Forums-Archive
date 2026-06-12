---
title: "Need to know how to recover files"
date: 2010-11-25
forum: General Help
---

### Post by Dipper on 2010-11-25
My 320 GB external hard drive has recently fallen victim to the Ubuntu USB startup disk utility.  I need to recover my files and cannot find the correct utility. Here is what I've used so far:

Foremost: Does an excellent job recovering photos, pdf files, and mpeg files.  Does not recover svg, openoffice, or music files

Magicrestore: Same as foremost, but recovers even fewer file types.  Maybe someone knows where I can find "recipes" for svg, odt, ods, mp3 files?

Photorec: Only recovers photos

Testdisk: Not sure how to use this, as the instructions are a bit too advanced for me.

So I desperately need a utility that will recover my openoffice, inkscape, and music documents.

---

### Post by s.shawky on 2010-11-25
you can use gparted cd 
it helped me before to restore my whole partition with all files and folders

---

### Post by Rubi1200 on 2010-11-25
Testdisk; more detailed instructions that I hope will help:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

---

### Post by oleink on 2010-11-25
> **Rubi1200 said:**
> Testdisk; more detailed instructions that I hope will help:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

+1

Used this to recover 320 gig external wd hd files + it's photo recovery counterpart is also very useful

---

### Post by sbergman on 2011-04-12
> **Dipper said:**
> .....

Foremost: Does an excellent job recovering photos, pdf files, and mpeg files.  Does not recover svg, openoffice, or music files

...

Hi there.

WRT openoffice files. Have a look at the foremost man page - it basically says that since oo files are simply zipped xml files, they'll appear under the zip file folder. Might not be practical if you have a billion zip files there, but at least your oo files are in there somewhere. As a guess I'd try 1st finding the zip file that's actually the oo file you're looking for, and simply rename it from .zip to .odt (or whatever is applicable). 

Similarly I would say that mp3 files would appear as mpegs.

Rgds,

---


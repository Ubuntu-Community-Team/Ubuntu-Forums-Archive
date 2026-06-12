---
title: "Google Earth?"
date: 2009-09-03
forum: General Help
---

### Post by BSG Fan on 2009-09-03
As you know Ubuntu doesn't install the program but only =creates a bin file (.deb file?)...
so


If I open the terminal and I type this:
"
make-googleearth-package  --file  Google EarthLinux.bin--force
"
it will install the package in my pc, no?
Now the question is:
how I can remove that program later?

ps: it's well written the code here or I put too much spaces?

---

### Post by misterfixit on 2009-09-03
> **BSG Fan said:**
> As you know Ubuntu doesn't install the program but only =creates a bin file (.deb file?)...
so


If I open the terminal and I type this:
"
make-googleearth-package  --file  Google EarthLinux.bin--force
"
it will install the package in my pc, no?
Now the question is:
how I can remove that program later?

ps: it's well written the code here or I put too much spaces?


When you locate the downloaded GE bin file, as administrator change the permission to allow executing, then do:

  ./Google* 

in the folder where the bin file is located.  That will execute the bin file and you will have GE.  At least that is what I have done several times and it works for me every time.  This assumes you have no other files beginning with the name "Google" in that download area, of course; otherwise, just type in the entire file name.

HTH, YMMV,

Dave

---

### Post by oldos2er on 2009-09-03
If you enable the Medibuntu repository ([http://medibuntu.org](http://medibuntu.org)) you can install GE from there.

---

### Post by BSG Fan on 2009-09-04
> **misterfixit said:**
> When you locate the downloaded GE bin file, as administrator change the permission to allow executing, then do:

  ./Google* 
in the folder where the bin file is located.  That will execute the bin file and you will have GE.  At least that is what I have done several times and it works for me every time.  This assumes you have no other files beginning with the name "Google" in that download area, of course; otherwise, just type in the entire file name.
HTH, YMMV,
Dave

===
I will try and I will let you know
Thanks you, MisterFixit
:)

---

### Post by BSG Fan on 2009-09-04
> **oldos2er said:**
> If you enable the Medibuntu repository ([http://medibuntu.org](http://medibuntu.org)) you can install GE from there.

===
I will try and I will let you know
Thanks you, Oldos2Er
:)

---


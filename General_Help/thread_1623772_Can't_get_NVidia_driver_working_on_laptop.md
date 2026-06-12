---
title: "Can't get NVidia driver working on laptop"
date: 2010-11-17
forum: General Help
---

### Post by smmalis on 2010-11-17
Pretty self explanatory, I can't get the NVidia driver to work with my laptop's 310M.  And yes I have tried both steps in [http://ubuntuforums.org/showpost.php?p=9965364&postcount=9](http://ubuntuforums.org/showpost.php?p=9965364&postcount=9), but to no avail.  The two error messges I'm seeing are "(EE) No devices detected." and "Fatal server error: no screens found".  Any ideas?

---

### Post by Vigh on 2010-11-17
did you remember to enable the new beta graphics card driver in->

system-> administration-> additional drivers

after following the steps

failing that, download the latest drivers directly from nvidia and install them through the terminal, it sounds hard but is relatively simple once you have done it once

---

### Post by dazman19 on 2010-11-17
Yep

wget [http://addressto.file/](http://addressto.file/)

then sh ./filename.run

follow the instructions. Then restart.

---

### Post by smmalis on 2010-11-17
Tried installing the latest drivers from NVidia's website, still no luck.  Same exact error messages.  Anyone else have any idea on how to fix this?

---


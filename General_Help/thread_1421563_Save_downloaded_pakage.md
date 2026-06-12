---
title: "Save downloaded pakage"
date: 2010-03-04
forum: General Help
---

### Post by uShafee on 2010-03-04
Hai. I am on a pretty slow connection. So i would like to keep a copy of files I have once downloaded offline. Where will files I download from terminal like this be saved at? (for example wine)

sudo apt-get install wine

and how would i run the file again?

---

### Post by oldos2er on 2010-03-04
Packages are saved in /var/cache/apt/archives. You can reinstall them with either dpkg or gdebi.

---

### Post by hachel on 2010-03-04
doesn't apt-get automatically check /var/cache... first before downloading?

---

### Post by uShafee on 2010-03-04
I am going to replace the hard disk.. so it wouldnt be in the cache folder next time

Thanks ;)

---

### Post by oldos2er on 2010-03-04
> **hachel said:**
> doesn't apt-get automatically check /var/cache... first before downloading?

I believe so.

---


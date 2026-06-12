---
title: "automatix killed my dvd collection"
date: 2006-01-31
forum: General Help
---

### Post by pedwards on 2006-01-31
after installing automatix i cant play any dvd's in my comp.  
it tells me i dont have libdvdcss 
WHAT DO I DOO?

---

### Post by jasmuz on 2006-02-01
sudo apt-get install libdvdcss

---

### Post by pedwards on 2006-02-01
because of the wonders of the automatix project my repo's are filled with many dead backports and repo's that are unresponsive, ive added all my standard ubuntu repo's but i still cant get libdvdccs

(apt-get install libdvdcss didnt work because automatix effed my repos)
is it ok to delete all the repo's that automatix adds?

---

### Post by aysiu on 2006-02-01
Just download it from [here](ftp://ftp.nerim.net/debian-marillat/pool/main/libd/libdvdcss/libdvdcss2_1.2.9-0.0_i386.deb) to your desktop, then ```
cd Desktop
sudo dpkg -i libdvd*.deb
```

---


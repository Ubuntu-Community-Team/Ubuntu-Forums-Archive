---
title: "Linksys WUSB11v4 wireless adapter"
date: 2006-01-24
forum: General Help
---

### Post by yochanan.g on 2006-01-24
Hello!
I have takes the following steps in trying to install this device:
1)Downloaded the atmel driver from here:
[http://at76c503a.berlios.de/cvs.html](http://at76c503a.berlios.de/cvs.html)

2)Ran the following commands
sudo apt-get install build-essential linux-headers-`uname -r`
tar xzvf at76c503a-cvsroot.tar.gz
tar xzvf at76c503a-cvsroot.tar.gz
mv at76c503a CVS
cvs -d `pwd`/CVS co at76c503a
cd at76c503a
make ... at this point I run into problems. I get several screens of errors and warnings.

Any advise would be appreciated.

---

### Post by nominal on 2006-01-24
I had the same problem, sorry never fixed it, i just screwed the damn wusb11 device and got a long ethernet cord--cheap at wal-mart.

---

### Post by KermitJr on 2006-01-31
OK,

I've done all the above... had to install cvs rcs and gcc-3,4 (other gcc didn'twork). Still nothing.

---


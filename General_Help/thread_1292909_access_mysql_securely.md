---
title: "access mysql securely"
date: 2009-10-16
forum: General Help
---

### Post by fabianus on 2009-10-16
Hello all !

I would like to access mysql from the public in a secure manner. Could you suggest me how to set this up?

Thanks a lot for any help !

Regards, 
Fabianus

---

### Post by blueridgedog on 2009-10-16
If you want command line access, then nothing beats ssh to your system then the standard mysql command line tools.

If it is web access you want, then you could either tunnel your web traffic over ssh or your could use https.

---


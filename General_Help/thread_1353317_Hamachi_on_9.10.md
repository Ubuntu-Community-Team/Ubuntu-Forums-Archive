---
title: "Hamachi on 9.10"
date: 2009-12-12
forum: General Help
---

### Post by Quarkrad on 2009-12-12
I seem to be going round in circles trying to get Hamachi working on 9.10.  Typing in hamachi-init results in:

**hamachi-init: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory**

some pages seem to have a fix/solved but I have tried them all - keep getting this response.  Has anybody got Hamachi to work n a clean install of 9.10?

---

### Post by Quarkrad on 2009-12-12
Solved....  copy _libstdc++.so.5_  _libstdc++.so.5.0.7_    _libstdc++.so.6_    _libstdc++.so.6.0.13_   from **/usr/lib**  to ** /usr/lib32**   so the four files are in both directories.  I ran the hamachi-init command and then had trouble with something called  **libssl0.9.7**   This was fixed by sudo su in terminal and entering the command **ln -s /usr/lib/libcrypto.so.0.9.8 /usr/lib/libcrypto.so.0.9.7**.  I then ran **hamachi-init** and it worked!

---


---
title: "32bit file versions for 64bit server"
date: 2010-07-01
forum: General Help
---

### Post by KLStringer on 2010-07-01
I'm setting up and configuring Dell Open Manage Server Administrator on a Dell r610 with Ubuntu 10.04 x64 and need to get x32 version of:

/lib/libsepol.so.1
/lib/libselinux.so.1
/lib/security/pam_unix.so
/lib/security/pam_nologin.so

Their from libsepol1, libselinux1, and libpam-modules and I'm not sure how to go about getting them, making sure their x32 bit and the same version as whats currently on the server.

Thanks in advance

---

### Post by cariboo on 2010-07-01
If they are in the repositories, you can get the 32-bit packages from [http://packages.ubuntu.com](http://packages.ubuntu.com).

---

### Post by KLStringer on 2010-07-01
Haha I was just coming back here to say that I found them at:

[http://packages.ubuntu.com/lucid/](http://packages.ubuntu.com/lucid/)

---


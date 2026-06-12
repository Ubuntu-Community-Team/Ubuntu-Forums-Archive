---
title: "Installing the proprietary fglrx driver disables 3D acceleration"
date: 2011-04-28
forum: General Help
---

### Post by NCLI on 2011-04-28
I have a Radeon HD 6600M, which works fairly well with the free driver, but it's too slow. However, installing the proprietary driver makes me lose 3D support, and the AMDCCC doesn't work, claiming that the driver doesn't work,

---

### Post by techunit on 2011-04-28
Not sure did you install the release from the repo or download the script?


because you have such a recent card download the script from the ATI site and install from there. Problem solved!

Also good luck with the rebuilding of your country. My heart goes out to you guys.

---

### Post by NCLI on 2011-04-28
> **techunit said:**
> Not sure did you install the release from the repo or download the script?


because you have such a recent card download the script from the ATI site and install from there. Problem solved!

Also good luck with the rebuilding of your country. My heart goes out to you guys.
I tried that already, here's what happens:
```
seph@seph-vaio:~$ '/home/seph/Downloads/ati-driver-installer-11-4-x86.x86_64.run' 
Created directory fglrx-install.jUlUYr
Verifying archive integrity... All good.
Uncompressing ATI Catalyst(TM) Proprietary Driver-8.841................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
=====================================================================
 ATI Technologies Catalyst(TM) Proprietary Driver Installer/Packager 
=====================================================================
Detected configuration:
Architecture: x86_64 (64-bit)
X Server: X.Org 6.9 or later 64-bit
Removing temporary directory: fglrx-install.jUlUYr
seph@seph-vaio:~$ 

```
No errors, no nothing.

Also, while I appreciate the kind remarks, I'm just staying in Japan for one year, I am not Japanese(Sadly).

---

### Post by techunit on 2011-04-28
Anyone in Japan has alot to deal with.

You likely need to run as root.

sudo sh <script here> that should help that will use the terminal interface. If you want the UI use gksu instead of sudo sh.

---

### Post by NCLI on 2011-04-28
Thanks a lot, that worked! It did ask for my password when I ran it as a normal user, but I guess that wasn't enough somehow.

---

### Post by NCLI on 2011-04-29
UPDATE: My problem is still not solved. I am dropped to 2D fallback mode, and the AMDCCC still says the driver isn't working, even with the newest version from their website.

---

### Post by NCLI on 2011-04-29
Bump.

---


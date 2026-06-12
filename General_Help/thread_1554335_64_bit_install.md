---
title: "64 bit install ?"
date: 2010-08-16
forum: General Help
---

### Post by elwayisgod on 2010-08-16
Hi,

I downloaded and installed Ubuntu 10.01 (Lucid Lynx) yesterday and am about to embark on a Virtual Box journey.  How do I know if I installed 64bit or not?  My laptop is 64 bit, I just don't remember choosing a 32 vs 64 option during install.  Is there a way to check?

---

### Post by marshmallow1304 on 2010-08-16
Look at the filename of the .iso you downloaded.

---

### Post by Fire_Chief on 2010-08-16
It depends on what version you downloaded. There is a radio button on this page [http://www.ubuntu.com/desktop/get-ubuntu/download]("http://www.ubuntu.com/desktop/get-ubuntu/download"). Choose which version you want (32-bit or 64-bit) and then download the appropriate ISO image.

You'll notice that it defaults to the 32-bit version.

If you look at the ISO you downloaded already, you'll be able to tell quickly which version you have. If you see i386 in the name like this ubuntu-10.04-desktop-**i386**.iso, then you have the 32-bit version. If it says ubuntu-10.04-desktop-**amd64**.iso, then you have the 64-bit version.

Cheers!

---

### Post by Fire_Chief on 2010-08-16
It depends on what version you downloaded. There is a radio button on this page [http://www.ubuntu.com/desktop/get-ubuntu/download]("http://www.ubuntu.com/desktop/get-ubuntu/download"). Choose which version you want (32-bit or 64-bit) and then download the appropriate ISO image.

You'll notice that it defaults to the 32-bit version.

If you look at the ISO you downloaded already, you'll be able to tell quickly which version you have. If you see i386 in the name like this ubuntu-10.04-desktop-**i386**.iso, then you have the 32-bit version. If it says ubuntu-10.04-desktop-**amd64**.iso, then you have the 64-bit version.

Cheers!

---

### Post by Fire_Chief on 2010-08-16
It depends on what version you downloaded. There is a radio button on this page [http://www.ubuntu.com/desktop/get-ubuntu/download]("http://www.ubuntu.com/desktop/get-ubuntu/download"). Choose which version you want (32-bit or 64-bit) and then download the appropriate ISO image.

You'll notice that it defaults to the 32-bit version.

If you look at the ISO you downloaded already, you'll be able to tell quickly which version you have. If you see i386 in the name like this ubuntu-10.04-desktop-**i386**.iso, then you have the 32-bit version. If it says ubuntu-10.04-desktop-**amd64**.iso, then you have the 64-bit version.

Cheers!

---

### Post by bowens44 on 2010-08-16
do uname -m in the terminal. If it has "x86_64" in the result you have installed the 64 bit version.

---

### Post by elwayisgod on 2010-08-16
crap it was i386...

uname -m gives me:  i686


:(   

Is it easy to uninstall and re-install?

---

### Post by hudsonl on 2010-08-16
> **elwayisgod said:**
> crap it was i386...

uname -m gives me:  i686


:(   

Is it easy to uninstall and re-install?


Sounds like you have done much customization yet ... so yes ... it's easy.

When you get to the part where you select the partitions ... select the same partition you did on the initial install (for dual boot) or Entire disk for Ubuntu only ... and overwrite your first installation

---


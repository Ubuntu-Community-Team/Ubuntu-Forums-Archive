---
title: "Potentially Dumb Question About Kernels"
date: 2010-09-09
forum: General Help
---

### Post by crokett on 2010-09-09
I have Ubuntu 10.04 32-bit installed - it is what my company supports.  I am wondering if I could just drop the 64-bit kernel on the current install and boot the current install to it?  I tried installing 64-bit along side but had problems installing some of my company's specific packages.

---

### Post by marshmallow1304 on 2010-09-09
Having never tried it, I don't know if it would work.  You could always try it then choose a different kernel at boot if it fails.  However, I don't think you'd see a lot of benefit from it even if it works.  If your company has 32-bit only .deb packages, you can force install on 64-bit Ubuntu by using
```
sudo dpkg -i --force-architecture /path/to/package.deb
```

You'll first need to install ia32-libs.

---

### Post by Ayuthia on 2010-09-09
All of your applications is currently compiled in 32-bit so it would not work right in the 64-bit world.  

Normally you need to reinstall if you want to switch.  You can backup your documents and other files (not applications though) and then restore them into your 64-bit system.

If you end up installing the 64-bit kernel in the system, most likely things will not work.

---

### Post by crokett on 2010-09-09
That's kinda what I figgered.  Thanks.  I will wait for 64bit support, if ever.

---

### Post by uRock on 2010-09-09
I reinstalled from 64 to 32bit for better functionality.:D

---


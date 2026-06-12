---
title: "how to get high resolution bootsplash when cryptsetup installed"
date: 2010-09-12
forum: General Help
---

### Post by patriot4 on 2010-09-12
Hello,

I've got a little problem. I'm using an nvidia graphic card, as i read before on this forum, to get high resolution in bootsplash i need v86d package - and i installled it and i get back 1680x1050 resolution in bootslash. But the problem with resolution come back after installing cryptsetup package, now i've got 640x480 and i can change it, I trying to reconfigure v86d , plymount, trying update-initramfs -u but with no result. Have you got some solution for this ?

---

### Post by nilsja on 2010-09-18
same problem here on a toshiba satalite L650D-11g...

---

### Post by echo6 on 2010-09-18
I believe update-initramfs is broken under 10.04, at least that has been my experience, it fails to recognise custom kernel or the new initrd-img file.

Try sudo update-intramfs -u -k `uname -r`

---

### Post by wiz561 on 2010-11-01
> **echo6 said:**
> I believe update-initramfs is broken under 10.04, at least that has been my experience, it fails to recognise custom kernel or the new initrd-img file.

Try sudo update-intramfs -u -k `uname -r`

I've tried this and it doesn't work.  :(

---

### Post by Frogs Hair on 2010-11-01
Sorry broken link

---


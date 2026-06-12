---
title: "Compiling the actual 2.6.15-23 kernel doesn't work"
date: 2006-06-01
forum: General Help
---

### Post by lemerou on 2006-06-01
I'm using the actual source from the repositories and I lanch the compilation with this command:

```
fakeroot make-kpkg --append-to-version=.010606 kernel_image --initrd binary
```

But after a moment this error occured

```
  CC [M]  drivers/usb/net/zd1211/zdusb.o
Dans le fichier inclus à partir de drivers/usb/net/zd1211/zdusb.c:41:
drivers/usb/net/zd1211/zddevlist.h:7:2: erreur: #error "Error in source file, line 35"
make[5]: *** [drivers/usb/net/zd1211/zdusb.o] Erreur 1
make[4]: *** [drivers/usb/net/zd1211] Erreur 2
make[3]: *** [drivers/usb/net] Erreur 2
make[2]: *** [drivers/usb] Erreur 2
make[1]: *** [drivers] Erreur 2
make[1]: quittant le répertoire « /usr/src/linux-source-2.6.15 »
make: *** [stamp-build] Erreur 2
```

---

### Post by lemerou on 2006-06-01
Ok error found!

apt-get install gawk linux-kernel-devel
fakeroot make-kpkg clean

and retry!

---


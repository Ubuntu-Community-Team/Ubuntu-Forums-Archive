---
title: "Syslinux - iscsi windows xp"
date: 2011-08-02
forum: General Help
---

### Post by tinkerbox on 2011-08-02
Hi guys,

Need your help again. I google for ages(coz i always feel lazy to open thread and alwayz believe in google), found lot of websites explaining this but I never success so far. I will explain..

I downloaded [http://www.kernel.org/pub/linux/utils/boot/syslinux/4.xx/syslinux-4.04.tar.gz](http://www.kernel.org/pub/linux/utils/boot/syslinux/4.xx/syslinux-4.04.tar.gz) and extract needed files to /tftpboot/

/tftpboot/ dir
```

cmd.c32
memdisk
menu.c32
pxelinux.0
sanboot.c32
vesamenu.c32

```

in dhcp added code
```
filename "pxelinux.0";
```

/tftpboot/pxelinux.cfg/default
```

label xp
  kernel sanboot.c32
  append iscsi:192.168.1.1:::0:iqn.2010-11.com.test:diskless.pc1

```

How to solve this?
[IMG]http://img34.imageshack.us/img34/7186/booterror.png[/IMG]


Forgot to mention. I successfully do this using gpxe @ ipxe. I just want to try this

---

### Post by tinkerbox on 2011-08-04
hmmm no one??

---

### Post by tinkerbox on 2011-08-09
bump..

---


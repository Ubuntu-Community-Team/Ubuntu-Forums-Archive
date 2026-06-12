---
title: "Reducing initrd size for faster boot on older systems"
date: 2010-05-02
forum: General Help
---

### Post by AwesomeTux on 2010-05-02
Hello,

I was curious, so I tried a few things to reduce the size of my initrd.img file to see if it would improve my boot time on an old system of mine with an IDE drive. And one thing seemed to help.

In the /etc/initramfs.conf file change:
```
MODULES=most
```

To:
```
MODULES=dep
```

This will make update-initramfs try and guess which modules to load.

After making the change, run:
```
update-initramfs -u -t
```

This reduced my initrd.img from 8.3 MB to 2.2 MB, and took about 5 seconds off my boot time on this older system.

!!DO THIS AT YOUR OWN RISK!!

Hope this helps someone.

-AwesomeTux

---


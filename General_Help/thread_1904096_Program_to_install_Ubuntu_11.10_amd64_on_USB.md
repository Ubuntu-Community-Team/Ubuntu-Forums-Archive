---
title: "Program to install Ubuntu 11.10 amd64 on USB"
date: 2012-01-04
forum: General Help
---

### Post by Numi on 2012-01-04
Hello everyone. I am having a really hard time figuring this out. But I have tried both Ubuntu 11.10 and presently have Fedora 16 on my laptop. The problem I am having is that I have decided that I would like to put Ubuntu 11.10 back on my laptop because I liked it better -less buggy than Fedora. The problem is that I can't find a program that works that way. I am trying to create a USB stick from the Ubuntu 11.10 64 bit ISO image. I tried Fedora Live USB Creator and selected the Ubuntu 11.10 image, but it failed on the checksum MDF file. Any suggestions?

---

### Post by dcstar on 2012-01-04
> **Numi said:**
> Hello everyone. I am having a really hard time figuring this out. But I have tried both Ubuntu 11.10 and presently have Fedora 16 on my laptop. The problem I am having is that I have decided that I would like to put Ubuntu 11.10 back on my laptop because I liked it better -less buggy than Fedora. The problem is that I can't find a program that works that way. I am trying to create a USB stick from the Ubuntu 11.10 64 bit ISO image. I tried Fedora Live USB Creator and selected the Ubuntu 11.10 image, but it failed on the checksum MDF file. Any suggestions?

Use this:

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by rjf1 on 2012-01-04
I used this -- worked as expected:

[https://github.com/abock/image-usb-stick](https://github.com/abock/image-usb-stick)

---

### Post by mikewhatever on 2012-01-04
You can also write the 11.10 ISO image with dd. For example:

```
sudo dd if=path_to_iso of=/dev/sdx bs=4096
```

---


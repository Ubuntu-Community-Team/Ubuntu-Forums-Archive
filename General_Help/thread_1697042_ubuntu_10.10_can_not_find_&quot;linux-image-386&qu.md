---
title: "ubuntu 10.10 can not find &quot;linux-image-386&quot; pkg"
date: 2011-02-28
forum: General Help
---

### Post by MK_muse on 2011-02-28
Hello everyone,

I have installed ubuntu 10.10 (2.6.35-25-generic) using a VM on an SD card to use it for my 486-class chip (Vortex86DX).
I guess I need to install the 486-class compatible kernel. But I can not find any package using the following command.
sudo apt-get -y install linux-386

any comment is appreciated.

Thanks you in advance,

---

### Post by DigitalDon on 2011-02-28
I have been running into similar problems. I have come to the conclusion that support for i386-i586 processors has been dropped in 10.10 hence why there is no package available.

I guess we will have to use an older version.

I dont know for sure that this is correct as I am no linux expert. Please correct me if I am wrong.

[http://www.webupd8.org/2010/06/ubuntu-1010-maverick-meerkat-wont-run.html](http://www.webupd8.org/2010/06/ubuntu-1010-maverick-meerkat-wont-run.html)

---


---
title: "How do I install kernel 2.6.33?"
date: 2010-05-05
forum: General Help
---

### Post by schwabdale on 2010-05-05
How do I do this without damaging my current installation of Ubuntu? Please post!

---

### Post by Ad@m on 2010-05-05
If you are running Ubuntu 10.04

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33.3-lucid/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.33.3-lucid/)

For Ubuntu 10.04 64-bit only
sudo dpkg -i linux-image-2.6.33-02063303-generic_2.6.33-02063303_amd64.deb
sudo dpkg -i linux-headers-2.6.33-02063303_2.6.33-02063303_all.deb
sudo dpkg -i linux-headers-2.6.33-02063303-generic_2.6.33-02063303_amd64.deb

For Ubuntu 10.04 32-bit only
sudo dpkg -i linux-image-2.6.33-02063303-generic_2.6.33-02063303_i386.deb
sudo dpkg -i linux-headers-2.6.33-02063303_2.6.33-02063303_all.deb
sudo dpkg -i linux-headers-2.6.33-02063303-generic_2.6.33-02063303_i386.deb

---


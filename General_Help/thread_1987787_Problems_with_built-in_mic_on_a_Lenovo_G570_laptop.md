---
title: "Problems with built-in mic on a Lenovo G570 laptop"
date: 2012-05-26
forum: General Help
---

### Post by handofdave on 2012-05-26
Can anyone help? I am very new to linux and have recently bought a lenovo g570 laptop and install ubunut 10.10. the mic work when windows was installed but know it doesn't. I'm in school beginning to study network systems and have-you that is why i installed ubuntu, to get a head start on everyone else(hopefully).

---

### Post by dino99 on 2012-05-26
its a known problem and recently the kernel team might have made some progress about it; so download and install the latest kernel from there:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/current/](http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/current/)

what you need to do:

- create an empty directory to download the required files , inside your /home user session :

 sudo mkdir kern

- download the 3 needed deb files from the given link, into that kern folder. You have to choose betwween i386 (32 bits) or amd64 (64 bits) packages. Myself prefer i386 right now as i use some exe apps, so it up to you, but rarely on 64 bits installation we get issue with some apps/drivers.

you need 3 deb:
- linux-headers.............all.deb
- linux-headers.............i386.deb  (or amd64.deb if you choose to install that one)
- linux-image................i386.deb  ( """"")

then into a terminal:

cd kern
sudo dpkg -i *

thats all, now you can reboot on that new kernel

---


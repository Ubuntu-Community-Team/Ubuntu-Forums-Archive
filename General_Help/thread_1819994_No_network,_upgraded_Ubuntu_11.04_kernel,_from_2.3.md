---
title: "No network, upgraded Ubuntu 11.04 kernel, from 2.3.38-10 to 2.6.39-4"
date: 2011-08-07
forum: General Help
---

### Post by helloicanseeu on 2011-08-07
hi, i installed 11.04 ubuntu 64bit,
was having problems with artifacts when resizing windows with compiz
and non working usb 3.0.

decided to upgrade kernel for better luck,
d/l and installed the following files
linux-headers-2.6.39-02063904_2.6.39-02063904.201108040905_all.deb
linux-headers-2.6.39-02063904-generic_2.6.39-02063904.201108040905_amd64.deb
linux-image-2.6.39-02063904-generic_2.6.39-02063904.201108040905_amd64.deb

did the necessary initramfs and update-grub, boot was as before upgrade,
but my networking cannot work at all, had to undo the 3 files in synaptic to get a working machine back.

tried a 'sudo modprobe r8169' and my 'eth1' came back, but just couldnt get networking started despite doing 'sudo /etc/init.d/networking restart'

i dont want to spend 10hrs digging at it, so what should i do with these new kernels?
i encountered the same problem with kernel 3.0.1 debs and even compiling and making debs from source code.

ubuntu is making me sick.

---

### Post by ~!geek!~ on 2011-08-07
For a temporary help, you may use one of the other kernels to boot from the grub loader screen (older ones). And try to remove the new kernel and reinstall this after successfully removing it.

---

### Post by helloicanseeu on 2011-08-09
nevermind, i somehow got the network under 2.6.39-4, i think it was the initramfs or rebuilding the r8168 nonbuggy code, very little decent documentation for these very impt things around ... lots of hype around ... all rubbish.

---


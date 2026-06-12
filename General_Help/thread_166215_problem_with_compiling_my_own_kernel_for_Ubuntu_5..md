---
title: "problem with compiling my own kernel for Ubuntu 5.10"
date: 2006-04-26
forum: General Help
---

### Post by leeyee on 2006-04-26
Hi guys,
I'm using Ubuntu 5.10 with the kernel 2.6.12-10-686 which was installed via apt-get from the official source. Now I'm wondering to compile my own kernel for my laptop with the kernel source downloaded from kernel.org (if I recall, it's called as vanilla kernel).
Well, as you know, to compile a custom kernel wants many many options to be selected properly. But unfortunately I'm not an expert of hardware, so many options come with the vanilla kernel are unfamiliar for me:confused: . So i have to post here, and want to know if i can use the default kernel options (I mean the config file) of the currently using kernel 2.6.12-10-686 as a cornerstone for my compilation. If i can, how to?
:-| And sorry for my poor English, I hope you can understand me.
Thank you in advance! :KS

---

### Post by leeyee on 2006-04-27
Well, It seems that no one has interest in this issue.....
I have made some progress of this, I just did:
```

[leeyee@myUbuntu:~/Software/kernel/linux-2.6.16.11]$cp /boot/config-2.6.12-10-686 .config
[leeyee@myUbuntu:~/Software/kernel/linux-2.6.16.11]$make oldconfig

```
After this was done, I configured the kernel options with "make menuconfig", and disselected some options and added some as well. However, things seemed worked fine untill i did "make modules_install" and "make install", I found that, after the installation of the new kernel, I couldn't find the initrd.img-2.6.16.11 file of the new kernel, and there was no difference of the /boot/grub/menu.lst file.
I want to know that, if there are any other things that i need to do before the initrd.img file can be appeared and the grub would recognize the new kernel? Thank you in advance!
Any help will be highly appreciated!

---


---
title: "Installing Atheros Ethernet Adapter into a new kernel"
date: 2012-03-05
forum: General Help
---

### Post by tim273 on 2012-03-05
Hi Everyone,

I have an Atheros Ethernet adapter and there is no driver built into the kernel (Ubuntu 10.04, kernel 2.6.32-38-generic).  I currently have it working using this fix:

[http://ubuntuforums.org/showthread.php?t=1677122](http://ubuntuforums.org/showthread.php?t=1677122)

However, each time I update the kernel, I have to recompile the driver...I can handle that.  What I was wondering is there any way to do this on a newly installed kernel (2.6.32-39-generic) before a reboot?  So I've done an apt-get dist-upgrade, the new kernel was installed, but I haven't rebooted yet.  I want to be able to install the module into that newly installed kernel so I can reboot with the ethernet adapter ready to go.

Anyway to do that?

Thanks,
Tim

---

### Post by idoitprone on 2012-03-05
I think i have that card and all i remember that 3.1 kernels an up support it. Well I always been using unstable cutting edge distros

look at dkms 
it will handle the recompile at update
[https://help.ubuntu.com/community/DKMS](https://help.ubuntu.com/community/DKMS)

---


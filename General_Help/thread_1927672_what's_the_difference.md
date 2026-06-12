---
title: "what's the difference?"
date: 2012-02-18
forum: General Help
---

### Post by Zerocool Djx on 2012-02-18
ok,.. I finally going to dual boot,........again


But, for some reason Ubuntu 10 and up the GUI won't load up. I have version 9.10 which has always been my favorite and it works. My question is, with all the customization these days of Ubuntu, what is the real difference between the current version of Ubuntu 11 over version 9.10? And please, forget talking about Unity, I think it's ugly and I will not use it. But other then that,.. what is the difference?

---

### Post by carl4926 on 2012-02-18
Newer kernel
Kernel modesetting

Adding 'nomodeset' to the boot argument might help you get to a UI, at least initially until you sort your graphics out

---

### Post by sudodus on 2012-02-18
Which GUI won't load up? Would it help to try some of the boot options discussed in this link?

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

One important difference is that drivers for new hardware has been added to the kernel in the new versions. Also there is more eye-candy in the 'vanilla' version. It needs more computing power than the old versions, but you have the choice of light-weight desktop environments: Xubuntu and Lubuntu to get a responsive computer, even if it is getting old.

Also, newer versions of the software packages are available for the newer versions of Ubuntu. (I'm talking about the software in the repositories.) But don't forget that 9.10 is no longer supported with updates, so security holes will not be repaired.

---

### Post by Zerocool Djx on 2012-02-18
So what on my computer wouldn't be compatable with the new kernel? I would be willing to upgrade that part, motherboard-CPU??

---

### Post by sudodus on 2012-02-18
> **Zerocool Djx said:**
> So what on my computer wouldn't be compatable with the new kernel? I would be willing to upgrade that part, motherboard-CPU??
Test with the boot options (nomodeset is one of them)!

And it certainly makes it easier for us to help, if you describe your computer.

---

### Post by Zerocool Djx on 2012-02-18
> **sudodus said:**
> Which GUI won't load up? Would it help to try some of the boot options discussed in this link?

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

One important difference is that drivers for new hardware has been added to the kernel in the new versions. Also there is more eye-candy in the 'vanilla' version. It needs more computing power than the old versions, but you have the choice of light-weight desktop environments: Xubuntu and Lubuntu to get a responsive computer, even if it is getting old.

Also, newer versions of the software packages are available for the newer versions of Ubuntu. (I'm talking about the software in the repositories.) But don't forget that 9.10 is no longer supported with updates, so security holes will not be repaired.


The live CD boots just fine, however one installed on the HD it won't load.

For refference: Dual core AMD 2.6, Radeon 5700 HD

---

### Post by sudodus on 2012-02-18
> **Zerocool Djx said:**
> The live CD boots just fine, however one installed on the HD it won't load.

For refference: Dual core AMD 2.6, Radeon 5700 HD

1. There are instructions how to use boot options also for ***installed*** systems.

2- There are often problems with Radeon graphics cards. Some problems can be solved with new proprietary graphics drivers.

---


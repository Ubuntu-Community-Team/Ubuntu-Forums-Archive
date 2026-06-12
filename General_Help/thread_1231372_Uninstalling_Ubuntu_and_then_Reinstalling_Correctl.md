---
title: "Uninstalling Ubuntu and then Reinstalling Correctly"
date: 2009-08-04
forum: General Help
---

### Post by apprentice789 on 2009-08-04
During the installation of Ubuntu something when wrong and I want to uninstall it from my computer and reinstall it correctly.  I uninstalled it from the add/remove in Window Vista but Ubuntu still shows up at the beginning of the start-up and still able to boot up when I restart my computer.  How do I completely uninstall Ubuntu?  I want to be able to reinstall a clean copy of Ubuntu on my computer. I want to have a dual boot with the option of booting to Window Vista or Ubuntu.  I also want to have Window Vista first in the booting hierarchy and Ubuntu second at this time until I completely change over to Ubuntu exclusively.  I will change the hierarchy of the boot then with Ubuntu first on the hierarchy.  I'm a complete novice so I don't understand much about partitiions and such.

---

### Post by wojox on 2009-08-04
Here's the dual boot doc:

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by apprentice789 on 2009-08-04
I don't understand.  Please explain in detail so I can understand the process to do what I'm trying to do.  Remember I'm a total novice.

---

### Post by philinux on 2009-08-04
> **apprentice789 said:**
> During the installation of Ubuntu something when wrong and I want to uninstall it from my computer and reinstall it correctly.  I uninstalled it from the add/remove in Window Vista but Ubuntu still shows up at the beginning of the start-up and still able to boot up when I restart my computer.  How do I completely uninstall Ubuntu?  I want to be able to reinstall a clean copy of Ubuntu on my computer. I want to have a dual boot with the option of booting to Window Vista or Ubuntu.  I also want to have Window Vista first in the booting hierarchy and Ubuntu second at this time until I completely change over to Ubuntu exclusively.  I will change the hierarchy of the boot then with Ubuntu first on the hierarchy.  I'm a complete novice so I don't understand much about partitiions and such.

Ok you're using wubi. What went wrong. It's possible to fix maybe without reinstall.

---

### Post by apprentice789 on 2009-08-04
No, all I want to do is uninstall Ubuntu out of my computer and then install it.  It doesn't matter if it kind of work now.  I just want the confidence that I have install Ubuntu correctly by starting over.  Like I said before, I want the option of booting from Windows Vista or Ubuntu and I want the default boot to be Window Vista for now.  How do I do all that?

---

### Post by Don1500 on 2009-08-04
> **apprentice789 said:**
> No, all I want to do is uninstall Ubuntu out of my computer and then install it.  It doesn't matter if it kind of work now.  I just want the confidence that I have install Ubuntu correctly by starting over.  Like I said before, I want the option of booting from Windows Vista or Ubuntu and I want the default boot to be Window Vista for now.  How do I do all that?

1st: get rid of the current installation of Ubunto: If you installed it in a partition this is easy. Open Ubuntu from the live CD. Go to System> options > Partition Manager (Gparted)
find your partition for Ubuntu and re-format it. Boom, Ubuntu is gone. If you are going to install Jaunty re-format as ext4 if you are installing anything else ext3.

2nd: Install Ubuntu onto the partition you just formatted. (Swap should be 2X RAM)

this should give you a dual boot system, but Ubuntu will be the default. After you sart up the first time in Ubuntu you can change this.
Go to System> Options> Startmanager> . In this GUI you can hunt around (there are only two panels) and find the default option. Change it to what you want.

---


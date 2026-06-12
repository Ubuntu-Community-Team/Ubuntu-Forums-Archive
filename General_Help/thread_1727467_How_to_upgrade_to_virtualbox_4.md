---
title: "How to upgrade to virtualbox 4"
date: 2011-04-12
forum: General Help
---

### Post by Pacopag on 2011-04-12
Hi. I have VirtualBox 3.2 and I'd like to upgrade to the latest version.  I'm using the one from the VirtualBox website, not the one in the repositories.

If I download the new package and try to install it, it says that there is a conflict (because I already have an older version installed).  I don't want to uninstall/reinstall because I don't want to lose the virtual machines already on there.

Is there a way to "upgrade" to VB 4.0 without losing it's configs and all?

Thanks,

---

### Post by pricetech on 2011-04-12
I have the same issue, but I just ignore the update and go on.

You shouldn't lose any machines by removing / installing vbox.  Your files should remain intact.

Back them up as a precaution and you should be just fine.

---

### Post by SeijiSensei on 2011-04-12
I just uninstalled virtualbox-3.2 before installing the new version.  Your virtual machines are safely stored in $HOME/.VirtualBox.  If you want to be sure, just make a copy of that entire directory.  If you have a bunch of VM's defined, run the backup overnight because it will take a while.

You should probably have a backup of this directory (indeed all of $HOME) just for safe keeping anyway.

---

### Post by Frogs Hair on 2011-04-12
Here are some links.

[http://www.ubuntugeek.com/virtualbox-4-0-released-and-ubuntu-10-1010-049-10-installation-instructions-included.html](http://www.ubuntugeek.com/virtualbox-4-0-released-and-ubuntu-10-1010-049-10-installation-instructions-included.html)

[http://www.unixmen.com/linux-distributions/4-ubuntu/1242-install-virtualbox-via-ppa-repository-in-ubuntu-1010-maverick-meerkat](http://www.unixmen.com/linux-distributions/4-ubuntu/1242-install-virtualbox-via-ppa-repository-in-ubuntu-1010-maverick-meerkat)

---

### Post by Telengard C64 on 2011-04-12
> **SeijiSensei said:**
> I just uninstalled virtualbox-3.2 before installing the new version.

This is what I did as well, except I upgraded from 3.0. I kept the old configuration files and everything worked great.

I installed the new version from the VirtualBox repository. First I removed the outdated repository from **/etc/apt/sources.list**. It looks like the key has not changed since Oracle took over, so my existing key was good. I did not install from the **virtualbox-4.0_*.deb** file.

[VirtualBox repository instructions for Ubuntu](http://www.virtualbox.org/wiki/Linux_Downloads)

I'm liking the cleaned up GUI  :D

---

### Post by Pacopag on 2011-04-12
Thanks for all the replies.  Can anyone tell me how to remove the existing version.  I've never removed a program that was installed from a .deb file.

---

### Post by Frogs Hair on 2011-04-12
> **Pacopag said:**
> Thanks for all the replies.  Can anyone tell me how to remove the existing version.  I've never removed a program that was installed from a .deb file.

Locate the package in the Synaptic Package Manager with the search , right click and mark for complete removal.

---

### Post by Telengard C64 on 2011-04-12
> **Pacopag said:**
> I've never removed a program that was installed from a .deb file.

```
sudo dpkg -r PACKAGENAME
```

I think that's how it goes anyway  ;)

---

### Post by Pacopag on 2011-04-12
It worked.  VMs are intact.  Thank you all.

---

### Post by JKyleOKC on 2011-04-12
Note that you need to also install the "extension package" from the Oracle website if you want USB and Guest Additions to work in vbox 4 the way they did in vbox 3's PUEL version...

---


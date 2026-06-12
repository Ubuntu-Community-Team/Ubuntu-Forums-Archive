---
title: "Problem Removing Printer Configuration GUI"
date: 2012-09-06
forum: General Help
---

### Post by amitbhalerao on 2012-09-06
Hello friends,

I don't use a printer so I wanted to remove all printing related packages.
I removed cups successfully using Ubuntu Software Center.

Then I tried to remove "Printing" (that's what USC says, package is system-config-printer-gnome). It warned me that it will also remove "ubuntu-desktop".
Synaptic Package Manager also warned me the same thing.

I have absolutely no problem letting it remain the same, but curious to know why ubuntu-desktop depends on a Printer configuration GUI.

Thanks,
Amit

---

### Post by MG&amp;TL on 2012-09-06
> **amitbhalerao said:**
> Hello friends,

I don't use a printer so I wanted to remove all printing related packages.
I removed cups successfully using Ubuntu Software Center.

Then I tried to remove "Printing" (that's what USC says, package is system-config-printer-gnome). It warned me that it will also remove "ubuntu-desktop".
Synaptic Package Manager also warned me the same thing.

I have absolutely no problem letting it remain the same, but curious to know why ubuntu-desktop depends on a Printer configuration GUI.

Thanks,
Amit


Hi Amit, 

The *ubuntu-desktop* package is a *metapackage*; that is, one that doesn't do anything in itself, but depends upon (and therefore installs) lots of other packages, such as the printer package. Metapackages are useful to install software bundles like the Ubuntu desktop.

It's safe to remove *ubuntu-desktop*, but do be careful if you choose to upgrade later as it can confuse the upgrade process.

---

### Post by amitbhalerao on 2012-09-08
Thanks MG&TL,

Though it is safe to remove, I'll let it remain in the system.

Thanks again,
Amit

---


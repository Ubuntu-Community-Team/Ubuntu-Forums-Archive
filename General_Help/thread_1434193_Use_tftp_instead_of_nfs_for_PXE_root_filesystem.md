---
title: "Use tftp instead of nfs for PXE root filesystem"
date: 2010-03-19
forum: General Help
---

### Post by bakegoodz on 2010-03-19
I have a custom Ubuntu distro that run both from a CD and PXE boot. The problem I have is that I need to boot in an environment that has to be routed through a router that can't forward NFS (the protocol doesn't use a standard port) I found that the Ubuntu based Clonezilla Live CD has a option like "fetch tftp://server/folder/filesystem.squashfs" I can borrow the kernel and initrd and it works, but how do I add this feature myself? Is there a package I need to install or a initrd option I need to add?

---

### Post by bakegoodz on 2010-07-16
I still missing all know how to do this all my self. I have to borrow the kernel and initrd from the Clonezilla live CD to make it work. Turns out busybox from busybox-initrd from doesn't have tftp support, but one from the regular busybox package does. Thanks to Steven @ Clonezilla for that bit of helpful knowledge.

---

### Post by cozhelp on 2012-02-14
How were you able to do it? What version of ubuntu and clonezilla did you use? I couldn't find the busybox-initrd. How did you work your magic? :confused:

---

### Post by bakegoodz on 2012-02-16
That was a year and a half ago, you expect me to remember that? It was probably Ubuntu Lucid 10.04 and a version of Clonezilla that uses used Lucid. I always use the alternative version of Clonezilla because it uses Ubuntu, unlike the standard version that uses Debian. I haven't looked at this for a least 6 months, but I think still holds true. The Clonezilla kernel will support loading the root file image via tftp, but the stock Ubuntu one won't. In my LiveCD/PXE Ubuntu respin I just swap the Ubuntu kernel and initrd files with the ones from Clonezilla. Did you have any other questions?

---


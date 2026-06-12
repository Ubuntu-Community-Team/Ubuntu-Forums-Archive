---
title: "clone to another drive using dd and install grub?"
date: 2012-04-16
forum: General Help
---

### Post by sdowney717 on 2012-04-16
[http://www.arsgeek.com/2008/01/22/how-to-clone-your-bootable-ubuntu-install-to-another-drive/](http://www.arsgeek.com/2008/01/22/how-to-clone-your-bootable-ubuntu-install-to-another-drive/)

How about the installing grub to that cloned drive, anyway to do this without having to download an entire install and burn to cd?

---

### Post by Herman on 2012-04-16
Maybe chroot into it from the installation you cloned it from?

---

### Post by oldfred on 2012-04-17
IF you do the dd from one drive to another the UUIDs will be the same. System will then have issues as it will not know which is which. I normally suggest a clean install and use rsync to copy your data from old /home to a new /home. You can copy the /home before the install and use it as part of new install.

Some have reported that it randomly uses one or the other depending on when BIOS gets drive up to speed. If you dd you have to disconnect old drive to avoid confusion.

You should always have a current liveCD or USB for every system you have installed. You never know when you have to make repairs and need a way to boot.

---


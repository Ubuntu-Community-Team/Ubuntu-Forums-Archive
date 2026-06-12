---
title: "vmware vs. virtualbox, start from different partition"
date: 2009-07-20
forum: General Help
---

### Post by manolo_asdf on 2009-07-20
hi,

inside ubuntu i want to load from an existing os-installation on a different partition.

virtualbox is for free but is it working OK starting os from an existing partition? is vmware more reliable here (though i guess vmware costs something).

---

### Post by TeamJ on 2009-07-20
I am starting the same project. I would use VMWare it is nicer, easier, more reliable. but I have heard on linux it can be slow. also, VMWare Server is free

---

### Post by bobince on 2009-07-20
> **manolo_asdf said:**
> virtualbox is for free but is it working OK starting os from an existing partition?

Yes, see [http://mesbalivernes.blogspot.com/2008/01/virtual-box-booting-from-existing.html](http://mesbalivernes.blogspot.com/2008/01/virtual-box-booting-from-existing.html) for some notes on this.

It is not necessarily a good idea, though. There's a fair bit of fiddling around you have to do to satisfy the Windows boot loader, and in any case Windows XP does not like being moved from one machine to another: if there are significant changes to the basic platform (and that's almost certain when you compare what VirtualBox emulates with your actual hardware) it is likely it won't start up at all.

There are annoying workarounds: see [http://www.virtualbox.org/wiki/Migrate_Windows](http://www.virtualbox.org/wiki/Migrate_Windows) for the basic shape of things. Since this requires changes to the Windows install you are probably safest cloning the partition to an image file and working with that anyway (see section 8.17 of the VirtualBox user manual) or just going for a clean install.

---


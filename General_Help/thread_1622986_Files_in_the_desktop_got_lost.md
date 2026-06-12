---
title: "Files in the desktop got lost"
date: 2010-11-16
forum: General Help
---

### Post by jjei on 2010-11-16
My laptop has Ubuntu 10.04 LTS running in a virtual machine. Just couple hours ago my computer ran out of batteries. When restarted it and started virtual machine and Ubuntu, 90% of stuff ithat was in my desktop is gone!!!

They are not on desktop and if I browse desktop with nautilus, the files are not there. They are not in the recent documents either.

Any suggestions??

---

### Post by mirearts KING SUNNY on 2010-11-16
A virtual machine normally don't save your files else if you save you files in a SHARED folder on a physical drive.

---

### Post by jjei on 2010-11-17
The virtual machine should not affect this. I mean, if I place items in the desktop they should stay there. And they have until now..

---

### Post by coffeecat on 2010-11-17
> **jjei said:**
> The virtual machine should not affect this.

Agreed. A virtual machine will have a /home/username/Desktop in the virtual filesystem, just like any non-virtual machine.

Virtual filesystems can suffer corruption just as much as actual ones from an unclean shutdown, which is probably what happened when your battery ran out. Have you tried booting in recovery mode and running fsck?

---


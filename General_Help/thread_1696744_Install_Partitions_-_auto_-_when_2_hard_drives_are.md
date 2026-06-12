---
title: "Install Partitions - auto - when 2 hard drives are...."
date: 2011-02-27
forum: General Help
---

### Post by ve2 on 2011-02-27
I have 2 hard drives. When I do an auto install Ubuntu decides to place partition on both hard drives... how do I prevent this -- without doing an auto config on partitions?

---

### Post by cain071546 on 2011-02-27
either partition manually, i assume your comfortable with Gparted 
or simply unplug the second HDD, install reboot/plug drive back in and format/partition as you wish

---

### Post by Mark Phelps on 2011-02-28
I'm guessing that you're trying to install Ubuntu to the "second" drive, but it's also installing GRUB (and the boot folder) to the "first" drive, right?

The suggestion to unplug the "other" drive is the simplest way to solve this -- and one I recommend as well.

---

### Post by desnaike on 2011-02-28
+1 After years of installs and undesired results unplugging one drive is indeed the way to go.

---


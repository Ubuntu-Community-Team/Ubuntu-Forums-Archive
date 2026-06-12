---
title: "Grub doesn't boot automatically"
date: 2012-02-15
forum: General Help
---

### Post by rockballad on 2012-02-15
Hello,

I've just installed Debian 6. I'm a fan of Ubuntu but I need Debian for XEN setup. They are both similar to each other so I'd like to post question here asking for help :P

I installed it from LiveCD. Grub was installed but it doesn't boot automatically. When I start my computer, the monitor shows:

grub >_

so i have to boot manually:

grub > chainloader +1
grub > boot

====
I generate menu.lst but it doesn't help.
So, how to make grub boots right after I start the computer?

Thanks in advance.

---

### Post by Vishnu V on 2012-02-16
Try re installing grub and update the grub
```

grub-install /dev/sda
update-grub

```

NB: you have to use sda or hda according to your harddisk type

---

### Post by rockballad on 2012-02-16
I did it, installed on MBR or /dev/sdb2 (it's on 2nd partition), update-grub and update-grub2 but none of them work. I'm so confused.

---

### Post by Vishnu V on 2012-02-16
Do you have two hardisk ?
for installing grub you need not want to specify partition 
only harddisk is needed , If you have two hardisk, install grub on primary hard disk

---

### Post by drs305 on 2012-02-16
Try using the Boot Repair app to fix things. If that doesn't allow the system to boot, it has an option to run the boot info script and will provide a link to a file called RESULTS.txt which will show us the status of your boot files.

Click the 'Boot Repair' link in my signature line for information about Boot Repair.

---

### Post by rockballad on 2012-02-16
Thanks, drs305. I'll check it ASAP.

yes, I have a laptop Windows7 running. Now I plug a HDD Box 2.5" into the laptop (via USB port) and install Debian on the second partition. 

First, I installed grub to the MBR of the first HDD (laptop). It replaces my Windows7 but I don't like it so I restored the MBR. Then, I installed grub to the second hard drive (external, partition 2). 

I have the laptop booted from external HDD first to make Debian run, but the screen shows grub prompt, waiting for me to boot manually.

I have another external HDD with Ubuntu 11. It works just fine so I'm confused with this HDD box.

Hope you see my issue now!

---

### Post by oldfred on 2012-02-16
Run the boot info script.

MBR is the first sector on a hard drive (sda, sdb etc) that the BIOS first jumps to, to start booting. It is before all partitions.

A PBR or partition boot sector (sda1, sda2, sdb1 etc) is the first sector of a partition and cannot be used for booting unless you have another boot loader that can chain load to it.

---

### Post by rockballad on 2012-02-16
Thanks, oldfred. So look like the issue is because of not installing grub on MBR of the second HDD. I know how to fix it now.

---


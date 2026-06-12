---
title: "Portable HD"
date: 2011-05-21
forum: General Help
---

### Post by adjbck on 2011-05-21
Ive been wondering about taking everything with me
which is why i invested in a Terabyte Portable HD.
Now im wondering if i can use the hd as a boot disk (possible)
and at the same time be able to search through all the files
and have the ability to view, edit, add and delete whatever i choose 

yours sincerely
a noob

---

### Post by ambdeep on 2011-05-21
you can partition your hdd and do all the stuff you wanted. or you can also have a single partition and install DiskInternal Linux reader in every system you intend to use the hdd with.

---

### Post by adjbck on 2011-05-21
> **ambdeep said:**
> you can partition your hdd and do all the stuff you wanted. or you can also have a single partition and install DiskInternal Linux reader in every system you intend to use the hdd with.

how would i go about partitioning it ?
any tutorials you could point to or a step by step
your time is greatly appreciated

---

### Post by ambdeep on 2011-05-21
you can try and use gaprted and partition your drive if you want a simple gui or you can also do it while installation by selecting manual installation. gparted should be installed by default in you ubuntu system, if not install it from the ubuntu software center. make sure you select the hdd for the installation of the boot manager or you might have problems booting.

---

### Post by adjbck on 2011-05-21
> **ambdeep said:**
> you can try and use gaprted and partition your drive if you want a simple gui or you can also do it while installation by selecting manual installation. gparted should be installed by default in you ubuntu system, if not install it from the ubuntu software center. make sure you select the hdd for the installation of the boot manager or you might have problems booting.

If i create two partitons one for my things and the other for the os + boot
how do i know which will do what
also if all that goes correct. How will i view my files
will there appear to be two portable hds or will it be go into the hd and i can choose which to access.

sorry for all the questions

---

### Post by ambdeep on 2011-05-21
the partition in which you will install ubuntu must be of the filesystem ext4. its size should be a minimum of 4 gb although i would suggest to keep atleast 20 gb. the other partition you can make to the filesystem ntfs so that it is compatible with all other operating systems. the bootloader is installed not in a partition but in the partition table of the hdd. while installing, simply select the hdd(not any of its partitions) when asked where you want to install the bootloader. also not that if you hdd doesnt boot after the correct installation, this is because the bios is pointing to the other hdds. to fix this simply go into the bios options and put the priority of usb devices above hdds.

---

### Post by adjbck on 2011-05-21
> **ambdeep said:**
> the partition in which you will install ubuntu must be of the filesystem ext4. its size should be a minimum of 4 gb although i would suggest to keep atleast 20 gb. the other partition you can make to the filesystem ntfs so that it is compatible with all other operating systems. the bootloader is installed not in a partition but in the partition table of the hdd. while installing, simply select the hdd(not any of its partitions) when asked where you want to install the bootloader. also not that if you hdd doesnt boot after the correct installation, this is because the bios is pointing to the other hdds. to fix this simply go into the bios options and put the priority of usb devices above hdds.

how would you personally go about installing it onto the hard drive from ubuntu
or would you do something else

---

### Post by ambdeep on 2011-05-21
first partition it using gparted like i said. then boot using the bootable cd and install it in the hdd.

---


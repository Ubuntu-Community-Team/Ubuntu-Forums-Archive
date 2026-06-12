---
title: "Sad day, I need to pull my Ubuntu partition and need help."
date: 2011-08-11
forum: General Help
---

### Post by GratefulDean on 2011-08-11
For the short time Ubuntu was usable on my system I loved it.  I used it for about 95% of my computing needs.  I enjoyed messing around with the command line and learning the ins and outs of what makes an OS tick.  Unfortunately I lost the GUI and have spent hours and hours over many months trying to get it back to no avail.

Now, I am having boot issues and my computer is acting weird.  I blame Windows for this as it is a perennial problem and the main reason I went to Ubuntu.  I use my laptop, my only computer, for work and any downtime, like loosing the GUI, really screws my world up.  So, I am going to remove Ubuntu from this machine.

How do I do this?  Can I just go to Windows and remove the partition?  What about the Grub?  This is my main concern as I get ulcers and flop sweats when my computer doesn't boot up.

Any help would be greatly appreciated.

PS. my wife has an old Dell desktop that she wants to replace as soon as she has the $$$, I do plan on putting Ubuntu on that machine when she does so this isn't good bye.

---

### Post by Carborundum on 2011-08-11
Depending on what your Windows partition table looks like you may be able to do what you want from within Windows. There is a partitioning tool somewhere in the Windows control panel, but you will not be able to make any changes to a mounted partition.

If you want to turn your Ubuntu partition into a new NTFS partition you can do that from within Windows.
If you want to extend a current NTFS partition that is not C: into your Ubuntu partition, you can do that from within Windows.
If you want to extend C: into your Ubuntu partition, you cannot do that from within Windows. You will need to use a tool such as GParted or Parted Magic to do this.

Removing GRUB and getting the normal Windows bootloader back will be more difficult. I'm afraid I do not know how to do this.

Edit
Looks like it should be possible to restore the Windows bootloader by booting from a Windows install disc and choosing "Repair", and then running the commands "fixboot" and "fixmbr", in that order. Google "remove grub restore windows bootloader" for more detailed explanations.

---

### Post by Jouke74 on 2011-08-11
You will get the problem that grub will not be able to find the Ubuntu partition so there won't be a bootable system. Read this

[http://www.makeuseof.com/tag/how-to-safely-uninstall-ubuntu-in-windows-dual-boot-environment/](http://www.makeuseof.com/tag/how-to-safely-uninstall-ubuntu-in-windows-dual-boot-environment/) 

So after deletion of your ubuntu partition within Windows you need to restore your MBR with the windows (rescue) CD.

---


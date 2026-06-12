---
title: "Hi and need help.."
date: 2012-02-19
forum: General Help
---

### Post by cainelethe on 2012-02-19
Hi everyone..
&#304; got a p4 3.00 cpu pc. i was using windows 7 ultimate and pardus 2011 for dual boot.
Last night i decided to erase pardus and install ubuntu for dual boot.
i erased (well,formatted) the part of hdd which are used by pardus.
and installed ubuntu that formatted place.. now my pc dont show the boot screen. and says
[COLOR=#000]GRUB Loading stage1.5
GRUB loading, please wait . . .
Error 17[/COLOR]

How can i solve it without formatting my whole hdd and windows 7 part?
Thanks for your help and sorry for my bad english.

---

### Post by iponeverything on 2012-02-19
boot from CD or USB drive that you used for the install. 

Choose "Boot from first hard disk"

then reinstall grub.

---

### Post by cainelethe on 2012-02-19
> **iponeverything said:**
> boot from CD or USB drive that you used for the install. 

Choose "Boot from first hard disk"

then reinstall grub.

i choosed and try it. it shows the grub error again then.

---

### Post by iponeverything on 2012-02-19
Boot the "try without installing option"

Then reinstall grub2 from live CD.

---

### Post by iponeverything on 2012-02-19
See here:

[https://help.ubuntu.com/community/Grub2#Use_Boot-Repair_Graphical_Tool](https://help.ubuntu.com/community/Grub2#Use_Boot-Repair_Graphical_Tool)

---

### Post by cainelethe on 2012-02-19
> **iponeverything said:**
> See here:

[https://help.ubuntu.com/community/Grub2#Use_Boot-Repair_Graphical_Tool](https://help.ubuntu.com/community/Grub2#Use_Boot-Repair_Graphical_Tool)

i downloaded boot-repair-disk.iso but i dont have a empty cd or dvd.
cant i do it from the usb flash stick which was ubuntu in it?

---

### Post by oldfred on 2012-02-19
See second option to install to Ubuntu.

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or post the link to a run of boot info script so we can see your exact configuration.

If you install to liveCD/USB it will not be saved, once you reboot.

---

### Post by cainelethe on 2012-02-19
> **oldfred said:**
> See second option to install to Ubuntu.

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or post the link to a run of boot info script so we can see your exact configuration.

If you install to liveCD/USB it will not be saved, once you reboot.

[[IMG]http://img35.imageshack.us/img35/3227/screenshotat20120219233.png[/IMG]](http://imageshack.us/photo/my-images/35/screenshotat20120219233.png/)

i got this screen.

---

### Post by oldfred on 2012-02-19
That is the install screen. You just want the try Ubuntu and add the Boot-Repair to the liveCD/USB so you can run it.

Unless you want to reinstall?

---


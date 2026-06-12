---
title: "Grub Boot Menu"
date: 2011-04-04
forum: General Help
---

### Post by scottyf11 on 2011-04-04
Hello,

I've searched on this topic and I can't get it to work.  I've changed the GRUB_DEFAULT=0 to GRUB_DEFAULT=3 in /etc/default/grub and I've installed startupmanager.  StartupManager says 10.10 is my default, but it still loads 9.04.  First I installed 10.10 then I installed 9.04.  As a result 9.04 is the first entry in Grub.  Is there a way I can change the order of the menu because for some reason the default parameter isn't working.

Thanks!!!

---

### Post by Kirboosy on 2011-04-04
After you made those changes to GRUB did you run the following command?
```
sudo update-grub
```

Also it sounds like you might have two different GRUBs installed. What is the grub Version that appears?


~Caboose

---

### Post by wilee-nilee on 2011-04-04
Both of these distros have different versions of grub so be prepared, boot to 10.10 and run these two commands.
sudo grub-install /dev/sda
then 
sudo update-grub

This will put the 10.10 as the grub2 controlling bootloader.  I have assumed sda here that would be if you have only one HD, if you have more then one determine the hd by running.
sudo fdisk -l

You're not looking for a number but the first 3 letters, the number is an actual partition, we want grub in the mbr.

---

### Post by scottyf11 on 2011-04-06
> **wilee-nilee said:**
> Both of these distros have different versions of grub so be prepared, boot to 10.10 and run these two commands.
sudo grub-install /dev/sda
then 
sudo update-grub

This will put the 10.10 as the grub2 controlling bootloader.  I have assumed sda here that would be if you have only one HD, if you have more then one determine the hd by running.
sudo fdisk -l

You're not looking for a number but the first 3 letters, the number is an actual partition, we want grub in the mbr.


Perfect!!! Thank you :)

---

### Post by techunit on 2011-04-06
please mark thread as solved.

---


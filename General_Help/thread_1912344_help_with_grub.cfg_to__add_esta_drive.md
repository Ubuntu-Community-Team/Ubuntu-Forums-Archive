---
title: "help with grub.cfg to  add esta drive"
date: 2012-01-20
forum: General Help
---

### Post by AlexMtl7 on 2012-01-20
I need help with grub2
I have laptop HP8540p with XP 
I external estata drive with another version of XP
I want to use dual boot
I installed grub2 to usb 
[http://h30434.www3.hp.com/t5/Notebook-Operating-Systems-and/Elitebook-8540w-won-t-boot-from-eSATA-drive/td-p/494633](http://h30434.www3.hp.com/t5/Notebook-Operating-Systems-and/Elitebook-8540w-won-t-boot-from-eSATA-drive/td-p/494633) 
please help me create grub.cfg (to add esta drive and enable boot form it)
Thank you
Alex

---

### Post by dcstar on 2012-01-20
> **AlexMtl7 said:**
> I need help with grub2
I have laptop HP8540p with XP 
I external estata drive with another version of XP
I want to use dual boot
I installed grub2 to usb 
[http://h30434.www3.hp.com/t5/Notebook-Operating-Systems-and/Elitebook-8540w-won-t-boot-from-eSATA-drive/td-p/494633](http://h30434.www3.hp.com/t5/Notebook-Operating-Systems-and/Elitebook-8540w-won-t-boot-from-eSATA-drive/td-p/494633) 
please help me create grub.cfg (to add esta drive and enable boot form it)
Thank you
Alex

Simply plug the eSata drive in so it is seen by the system (for SATA Hotplug you must have EHCI set in your BIOS) and then run the following command:

```
sudo update-grub
```

All drives with bootable partitions will be added to the Grub menu.

---


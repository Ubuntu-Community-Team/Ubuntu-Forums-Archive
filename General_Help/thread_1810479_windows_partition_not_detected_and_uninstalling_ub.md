---
title: "windows partition not detected and uninstalling ubuntu 11.04"
date: 2011-07-23
forum: General Help
---

### Post by blinkeyblock on 2011-07-23
i had windows 7 pre-installed in my laptop. i installed ubuntu 11.04 by making a bootable disk and did the partitioning so that both windows and ubuntu boot options would come on startup. 

however , when i switch on the laptop . the options do not come and ubuntu boots as if it is the default. i thought this might be due to a problem with grub 2 so i re-installed it. yet there was no difference.

i want to uninstall ubuntu now. but how do it? most guides require me to access windows and create a rescue disk and changing the MBR. but since i cant access my windows partition this isnt an option.

so there are 2 options for me - to make grub detect windows during boot and then use windows to make the MBR rite or to delete the system files of ubuntu to make it unbootable ?

---

### Post by Quackers on 2011-07-23
In Ubuntu open a terminal and run ```
sudo update-grub
``` and watch the terminal as grub.cfg is run. Is the Windows Loader recognised? If it is, reboot and you should now see a grub menu with the choice of which OS to boot.

---

### Post by blinkeyblock on 2011-07-24
thanx

---

### Post by Quackers on 2011-07-24
You're welcome :-)
If the matter is solved please mark the thread as solved using Thread Tools near the top of the page.

---


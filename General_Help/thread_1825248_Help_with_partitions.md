---
title: "Help with partitions"
date: 2011-08-15
forum: General Help
---

### Post by engrin on 2011-08-15
When I installed Ubuntu, I chose the option for Ubuntu only installation and I didn't partition my drive. I now want to add Windows 7 on a new partition. I want to know if it is possible to create a partition after the fact and how to do so? Thanks in advance for any help or suggestions :) Here is a screenshot of the drive's situation..
[IMG]http://img30.imageshack.us/img30/219/screenshot1dsw.png[/IMG]

---

### Post by fuzzyworbles on 2011-08-15
boot the machine with a live cd and run gparted. resizing the partitions should be self explanatory. 

installing 7 will overwrite the grub MBR. to fix this, you'll have to re-install the grub MBR after installing 7. this can be done a few different ways, but will always require booting once again off the ubuntu live cd. searching the forums will retrieve a slew of instructions on how to actually reassert grub on the MBR.

---

### Post by fdrake on 2011-08-15
i would sugest you to install first win 7 and the ubuntu if you don't have any import files(or just backup them). but if you really want to install win 7 after ubuntu read the section install Win after Ubuntu from the link:
[https://help.ubuntu.com/community/WindowsDualBoot#Installing%20Windows%20After%20Ubuntu](https://help.ubuntu.com/community/WindowsDualBoot#Installing%20Windows%20After%20Ubuntu)

---


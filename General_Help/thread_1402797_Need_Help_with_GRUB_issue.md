---
title: "Need Help with GRUB issue"
date: 2010-02-09
forum: General Help
---

### Post by reb716 on 2010-02-09
I know nothing about this at all. I have never programmed a computer.. I loaned my tower to a friend who put this on ...now i have it back and cant get to my windows 98. all i get each time i boot is ...
 
GRUB loading....
error:no such disk
grub recover>
 
I have tried ubuntu sec 8.4 recover mode and all i get is unreconized command..
i do not know how to set anything..
 
i have no disks for this not even the orginal windows recover disk..
 
is their anything i can do to get win to run as it use to??
 
please give a line by line if i need to program this...
 
thank you for any and all help

---

### Post by mikewhatever on 2010-02-09
From what you posted, it's not quite clear what the current setup is. Why not ask the friend what happened? In case you have Ubuntu installed, open Applications->Accessories->Terminal and post the output of the following commands:

sudo fdisk -l

tail -n 30 /boot/grub.menu.lst

---


---
title: "Dual boot Windows XP with Ubuntu"
date: 2010-06-23
forum: General Help
---

### Post by karthikn on 2010-06-23
I have dual booted Windows XP with Ubuntu .
First Windows Xp . 
After my Ubuntu  installation completed , i restarted the computer .
I chose Windows  XP in the boot manager .
But my Windows XP is not functioning .
I get a  Blue screen stating that Windows could not start .
Have I made any mistake during partitioning .
Guys,please help  me in solving this problem at the earliest .

---

### Post by varunendra on 2010-06-23
post here the output of the following command:```
sudo fdisk -l
```

EDIT: Also post the contents of /boot/grub/grub.cfg

---

### Post by wilee-nilee on 2010-06-23
> **karthikn said:**
> I have dual booted Windows XP with Ubuntu .
First Windows Xp . 
After my Ubuntu  installation completed , i restarted the computer .
I chose Windows  XP in the boot manager .
But my Windows XP is not functioning .
I get a  Blue screen stating that Windows could not start .
Have I made any mistake during partitioning .
Guys,please help  me in solving this problem at the earliest .

Post the bootscript in my signature in code tags.
[noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.
This will let us know a lot more then the fdisk command.

Also did you resize XP and install Ubuntu in it's own partitioned space from a booted live cd, and if you did; did you resize XP with the partitioner without rebooting XP before installing Ubuntu. Did you defrag XP befor you did any of this.

---


---
title: "Can I take over a Windows Partition?"
date: 2011-11-23
forum: General Help
---

### Post by Stupendous man on 2011-11-23
Hello
I have Ubuntu 11.10 installed as a dual boot with Windows XP.
I no longer use the windows install. I want to expand the Ubuntu partition and take over the Windows one, without having to re-install the whole thing. Is there a way to just tell Ubuntu that you want to absorb all other partitions, and remove the OS selection menu that shows on Boot?

---

### Post by LinuxFan999 on 2011-11-23
Download the gparted live CD ISO image from the gparted website, then burn the ISO image to a CD. Boot from the newly created CD and open gparted. Delete the Windows partition, move the Ubuntu partitions to the beginning and expand the / partition (and the /home partition if it exists. Next, save the changes and reboot (make sure to remove the CD). Boot into Ubuntu, open the terminal and type in this command:
```
sudo update-grub
```
Reboot and the Windows entry should be gone.

---


---
title: "Ubuntu is running in low graphics mode"
date: 2010-09-02
forum: General Help
---

### Post by RValente on 2010-09-02
[Asus 3500E Intel Pentium M Processor 740]
[Dual boot Ubuntu 10.04/Windows XP]

Hello Ubuntu community :)
After  a while reading about windows managers I tried to install another  windows manager (WM) besides the GNOME, the XFCE,  and another package  to allow me to chose the WM in the startup but as I reboot and didn't  saw any new WM I removed some packages including "wmanager", then I  reboot and I got this message "Ubuntu is running in low graphics mode" 

I have the Ubuntu Live USB with 2GB for persistence mode but no "Rescue broken system mode" included
- How can I add it to the Ubuntu Live USB stick
-  Or is possible to edit the boot files in order to set the boot to the  previous settings. I try to execute the [sudo apt-get update]
[sudo apt-get upgrade]
[sudo apt-get install -f]
[sudo apt-get autoremove]
but seems it doesn't have any effect once the output is [0 updated, 0 updated, 0 removed ...]


Summary:
1-Switch on
2-Dual boot menu (Pic_01)
3-Choose the updated generic and recovery modes and the same on old entries too  
4-Get a message with "Ubuntu is running in low graphics mode" (Pic_02)
5-Press  OK and end up in another window with different options but doesn't lead me nowhere. After I have chosen "Restart X" it ask me for login and passwd but  I'm not able to use package tools command as I described and I don't  know how to solve it without GUI. 

I also tried:
[sudo update-grub]
[grub-probe -t device /boot/grub]
[sudo grub-install /dev/sda3]
but it prompted an message saying that it's not possible (Pic_07) the same as when I tried inside Ubuntu Live USB in [sudo chroot /mnt] as explained in [https://help.ubuntu.com/community/Grub2#Command%20Line%20and%20Rescue%20Mode](https://help.ubuntu.com/community/Grub2#Command%20Line%20and%20Rescue%20Mode)


I would be glad for any help beside my question may be vague.

---


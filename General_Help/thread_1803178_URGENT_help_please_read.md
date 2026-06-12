---
title: "URGENT help please read"
date: 2011-07-12
forum: General Help
---

### Post by noidea24 on 2011-07-12
Im not new to ubuntu or computing itself but here is my situation, i had XP home and XP pro on my computer, i edit my boot.ini to boot straight to xp pro because i was going to format xp home for ubuntu. well i ended up formatting xp pro (lots of important files down the drain) in result of me rushing. well now right on boot it loads ubuntu i need to know how to boot into xp home or at least add the option to boot xp home. i really dont want to do another installation of xp because on this dell it take forever. anyhelp? please and thank you!

---

### Post by DHAines56 on 2011-07-12
When you boot your computer does it come up with a dual boot option, GRUB or other. If not you could try getting/making a windows recovery disk or simply put in your windows setup disk on boot and try repairing the install of XP Home. Also check the Windows partition/drive in Ubuntu to see if it has a boot.ini

---

### Post by wildmanne39 on 2011-07-12
> **noidea24 said:**
> Im not new to ubuntu or computing itself but here is my situation, i had XP home and XP pro on my computer, i edit my boot.ini to boot straight to xp pro because i was going to format xp home for ubuntu. well i ended up formatting xp pro (lots of important files down the drain) in result of me rushing. well now right on boot it loads ubuntu i need to know how to boot into xp home or at least add the option to boot xp home. i really dont want to do another installation of xp because on this dell it take forever. anyhelp? please and thank you!Hi, lets try the easy method first boot the ubuntu then run this command in a terminal
```
sudo update-grub
```
then restart you system and see if you get a menu to choose which one to boot.

---

### Post by JedMeister on 2011-07-12
TBH if XP Home isn't showing up in GRUB (after double-checking by running update-grub first) then I'd guess you have overwritten the whole boot system for XP (overwritten it with your Ubuntu install). If that's the case you may need to move your Ubuntu partition and create a new partition at the start of the disk and reinstall Win there (AFAIK Win needs certain files on the first partition to boot?). If you do that it should allow you access to your current XP Home install.

If you boot off an XP CD into recovery console, then run 'fixmbr" and 'fixboot' and reboot your system that may fix XP. If it does then you can use an Ubuntu LiveCD to repair GRUB so you can boot both.

---

### Post by noidea24 on 2011-07-13
@DHAines56
    Yes grub does come up with 4 option, ubuntu, ubuntu safemode, memtest 86, and something else. (may   not be exact but its along those line. and im pretty sure i still have the boot.ini file because i havent deleted it, i will try your suggestion with the repair.

@wildmanne39
    I tried the command but i get an error saying "/usr/sbin/grub-probe: error: cannot stat `aufs' " i tried restarting even though command was not succesful and nothing

@JedMeister
    no i have not over written the xp home partition i can still access it through ubuntu. i am going to log off and try the cd repair now, if you have any more tips please post them. 


Thanks for the replies!

---


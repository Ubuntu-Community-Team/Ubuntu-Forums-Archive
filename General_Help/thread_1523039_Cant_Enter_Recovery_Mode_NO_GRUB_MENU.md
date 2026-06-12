---
title: "Cant Enter Recovery Mode:: NO GRUB MENU"
date: 2010-07-03
forum: General Help
---

### Post by lordbux on 2010-07-03
I used to have a grub menu with options of
*Ubuntu
*Ubuntu Recovery Mode
*Memtest
and
*Windows

but later I installed Ubuntu alone on a machine , 
and i do not have GRUB menu. and i  want to enter the Recovery mode.

Please help.

---

### Post by synapsys on 2010-07-03
Boot from the liveCD (the one you used to install ubuntu) and choose the option to "try ubuntu with making any changes yada yada" 

You can then re-install grub from the liveCD.

Here are some instructions for reinstalling Grub2 (Karmic Koala and above)
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

Here are some instructions for grub legacy (before Karmic Koala)
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Good luck.

---

### Post by lordbux on 2010-07-03
> **synapsys said:**
> Boot from the liveCD (the one you used to install ubuntu) and choose the option to "try ubuntu with making any changes yada yada" 

You can then re-install grub from the liveCD.

Here are some instructions for reinstalling Grub2 (Karmic Koala and above)
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

Here are some instructions for grub legacy (before Karmic Koala)
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Good luck.

I did not use a live CD, i used the Alternate Disk.
and i dont think reinstalling will help and grub is working and the OS is loading .. but dont have the Grub Menu.

---

### Post by synapsys on 2010-07-03
Ah so.....

I believe, if i remember correctly (it's been so long since i've only had one os on a computer) that if you only have ubuntu installed then grub automatically boots unless you hit 'esc' while its booting. Either that or the timeout is set to 0 seconds or something, you can change that in startup manager. 

If you don't have it yet:
```
sudo apt-get install startupmanager
```

---

### Post by artemyv on 2010-07-03
> **lordbux said:**
> I did not use a live CD, i used the Alternate Disk.
and i dont think reinstalling will help and grub is working and the OS is loading .. but dont have the Grub Menu.
Probably - the menu is just hidden - you can press esc or shift button while in the bios boot screen to show it

If you want it to be shown always - you will need to read about grub (or grub2 if you use it ) options.

---

### Post by lordbux on 2010-07-03
> **artemyv said:**
> Probably - the menu is just hidden - you can press esc or shift button while in the bios boot screen to show it

If you want it to be shown always - you will need to read about grub (or grub2 if you use it ) options.


It seems i dont have a menu.list file in my grub folder.

---

### Post by sisco311 on 2010-07-03
> **lordbux said:**
> It seems i dont have a menu.list file in my grub folder.

Hold down the Shift key during the bootup.

[uhelp]community/Grub2[/uhelp]

---

### Post by artemyv on 2010-07-03
> **lordbux said:**
> It seems i dont have a menu.list file in my grub folder.
it could mean you have a grub2 which uses different files - please refer to the following thread for details

[http://ubuntuforums.org/showthread.php?t=1195275&highlight=grub2+guide](http://ubuntuforums.org/showthread.php?t=1195275&highlight=grub2+guide)

---

### Post by lordbux on 2010-07-04
> **artemyv said:**
> it could mean you have a grub2 which uses different files - please refer to the following thread for details

[http://ubuntuforums.org/showthread.php?t=1195275&highlight=grub2+guide](http://ubuntuforums.org/showthread.php?t=1195275&highlight=grub2+guide)



editing /etc/default/grub helped, thanks a lot

---


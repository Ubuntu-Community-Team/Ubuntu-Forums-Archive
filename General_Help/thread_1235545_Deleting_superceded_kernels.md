---
title: "Deleting superceded kernels?"
date: 2009-08-09
forum: General Help
---

### Post by aquascrotum on 2009-08-09
I'm dual booting XP with Jaunty, so at startup I get the list of OS's to pick from.  Following an update this morning I now have 6 9.04 kernels - presumably 5 of these are no longer needed, so how do I go about deleting them?

Cheers

---

### Post by coldReactive on 2009-08-09
It should be

```
sudo apt-get autoremove
```

---

### Post by wizardks on 2009-08-09
use command uname to get current kernel

use package manager to remove them

i keep the latest 2 kernel just in case the update has problems

---

### Post by martinbaselier on 2009-08-09
sudo apt-get autoremove won't remove old kernels. It will only remove packages, on which no other package depends. 

The package manager (synaptic) is the easiest way. Just search for linux-image

---

### Post by sandman55 on 2009-08-09
Why delete them just edit them out by placing a # in front of them then if you want to change it you can just remove the # 
 first you need to back up your grub so that if something goes wrong you have a good copy of grub so in a terminal type sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup then you will have to put in your password.

Now to see if you have made your backup OK click on places > Home folder > click the up arrow twice open the boot file then the grub file and you should see that you have a Menu.lst and a Menu.lst_backup close the window 

Now in terminal type sudo gedit /boot/grub/menu.lst and in the gedit file (I have posted my gedit file) you can see the kernals in groups for example the one you need to keep has the cursor in it example leave title,uuid,kernel,initrd,and quiet untouched I would also leave the next group recovery mode untouched but with the others if you put a # to the left of the line then they are edited out be careful not to edit out your windows when your done save at the top of the gedit page

also while you are here if you want to set your computer to boot to windows first you will see about 13 lines down from the top Default 0 take note of it and then reboot when you get to the grub page count the lines starting with 0 example if there are 3 lines you count 0 1 2 and end up with the number 2 depending on how many lines you have edited out.
Now go back to your grub gedit screen and replace the Default 0 with default number you came up with then save.
The only drawback with changing Default 0 is when your system downloads another kernel you have to either edit out the old one or change your Default number

---

### Post by martinbaselier on 2009-08-09
Each kernel takes up 100MB. If you don't use them, it's better to delete them. Just keep 2 or 3 kernels, so you'll have a backup if you mess up your current kernel.

---

### Post by drs305 on 2009-08-09
I'd recommend using StartUp-Manager if you aren't comfortable with editing system files. It can set the number of kernels to display, the default OS or kernel, and much more.

The StartUp-Manager guide linked in my signature line (SUM) tells you how to install it, how to set the number of kernels displayed in the menu, how to remove older kernels from the system and /or the menu, and more. It also provides some help if you wish to edit the menu manually.

---

### Post by sandman55 on 2009-08-09
> **drs305 said:**
> I'd recommend using StartUp-Manager if you aren't comfortable with editing system files. It can set the number of kernels to display, the default OS or kernel, and much more.

The StartUp-Manager guide linked in my signature line (SUM) tells you how to install it, how to set the number of kernels displayed in the menu, how to remove older kernels from the system and /or the menu, and more. It also provides some help if you wish to edit the menu manually.
I just checked it out, what an easy way to do things.

---

### Post by lidex on 2009-08-09
Another vote for Synaptic and boot options through StartUp-Manager. I only keep the two latest kernels. An easy way to change default OS boot is with grub-choose-default, available in universe repository.

---

### Post by scouser73 on 2009-08-09
> **aquascrotum said:**
> I'm dual booting XP with Jaunty, so at startup I get the list of OS's to pick from.  Following an update this morning I now have 6 9.04 kernels - presumably 5 of these are no longer needed, so how do I go about deleting them?

Cheers

Look at this tutorial for removing old kernels - [[COLOR="Red"]**Removing Old Kernels**[/COLOR]]("http://tombuntu.com/index.php/2007/10/17/remove-ubuntu-kernels-you-dont-need/").

---

### Post by aquascrotum on 2009-08-11
> **drs305 said:**
> I'd recommend using StartUp-Manager if you aren't comfortable with editing system files. It can set the number of kernels to display, the default OS or kernel, and much more.

The StartUp-Manager guide linked in my signature line (SUM) tells you how to install it, how to set the number of kernels displayed in the menu, how to remove older kernels from the system and /or the menu, and more. It also provides some help if you wish to edit the menu manually.

Just the job.  All sorted now, Grub shortened and 5 old kernels gone freeing half a gig of diskspace! Thanks!

---


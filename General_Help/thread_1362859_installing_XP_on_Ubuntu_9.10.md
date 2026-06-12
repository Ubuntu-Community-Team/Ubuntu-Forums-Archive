---
title: "installing XP on Ubuntu 9.10"
date: 2009-12-23
forum: General Help
---

### Post by Girdi on 2009-12-23
Hi everyone,  I have a 500GB HDD on one half I have installed Ubuntu 9.10 and now I want to install on the other half of the HDD Windows XP the last time I did it Grub was totaly overvritten by windows  my question is how to restore grub after that?

---

### Post by fjm03 on 2009-12-23
Yes.

Install XP first and then install Ubuntu.

---

### Post by Girdi on 2009-12-23
I dont want to install ubuntu again

---

### Post by hyperdude111 on 2009-12-23
It is quite an easy process.

**You will need a ubuntu live CD at hand**

First Install WinXP to the empty partition. This will overwrite ubunu's grub bootloader but do not worry.

Shutdown and boot into ubuntu from the live cd and go to terminal.
Type in terminal:

"sudo grub"
"grub> find /boot/grub/stage1"

That should return your Ubuntu partition in the form of (hdX,Y), use that:

grub> root (hdX,Y)
grub> setup (hd0)
grub> quit

(you don’t need to type the grub> bit)

That has re-installed grub but you can no longer see Windows XP

Now you need to configure Grub
Go to terminal from normal ubuntu and type :

“sudo gedit /boot/grub/menu.lst”

A large text file will open and at the bottom leave a line and add this:

title Windows XP
root (hd0,1)
savedefault
makeactive
chainloader +1

If this does not work it is because the wrong number is in place under root. If it fails boot into the live cd again and follow the steps from "Configure Grub" and under root try Combinations:
(hd0,0)
(hd0,1)
(hd0,2)
(hd0,3)
(hd0,4)

Good Luck

---

### Post by Girdi on 2009-12-23
I havent started the instalation yet, cause i didnt find /boot/grub/menu.lst this file :D:D:D maybe i have another version of grub

---

### Post by hyperdude111 on 2009-12-23
> **Girdi said:**
> I havent started the instalation yet, cause i didnt find /boot/grub/menu.lst this file :D:D:D maybe i have another version of grub

Ah yes, sorry in karamic they have grub 2. That is an easier process. I will try to find details on grub 2 which I am less familiar with.

---

### Post by lmarmisa on 2009-12-23
You can read here an alternative method based on a backup of the code area of the Master Boot Record:

[http://ubuntuforums.org/showthread.php?p=8549409](http://ubuntuforums.org/showthread.php?p=8549409)

---

### Post by hyperdude111 on 2009-12-23
Try this guide [http://ubuntuguide.net/how-to-restore-grub-2-after-reinstalling-windows-xpvistawin7](http://ubuntuguide.net/how-to-restore-grub-2-after-reinstalling-windows-xpvistawin7) it looks promising. 

Unfortunately I can not recommend which section to chose or the reliability of the guide because my grub 2 experience is quite limited.

However on xmas when my new hard drive arrives I will set up a win7 and ubuntu dualboot again so i will hopefully familiarize myself with the workings of grub2.

Good luck.

---

### Post by wilee-nilee on 2009-12-23
And here is the Grub2 wiki that has the information and more, click on Reinstalling from LiveCD if the page doesn't open at that place on the page.
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

You might also consider running XP in a virtual if you have enough memory.

---

### Post by running_rabbit07 on 2009-12-23
When you install XP, you will have to reinstall Grub2, because MS will write over it. Make sure when you install XP it is on a Primary partition. MS doesn't like being logical, pun intended. I just installed Windows 7 and had to reinstall grub, but it was for Ubuntu 9.04. I am not sure if the process is the same for installing grub2, but it should be the same as grub 1.5. It is configuring the grub file that is different.

---

### Post by Girdi on 2009-12-23
thx guys for help :-)))) it seem promissing I will try it tomorow for today I had enought of linux good night, and merry Xmas

---

### Post by running_rabbit07 on 2009-12-23
> **Girdi said:**
> thx guys for help :-)))) it seem promissing I will try it tomorow for today I had enought of linux good night, and merry Xmas
After you reinstall grub you will have to run```
sudo update-grub2
```

---


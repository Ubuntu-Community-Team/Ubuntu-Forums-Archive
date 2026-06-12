---
title: "Freeze after login."
date: 2012-06-17
forum: General Help
---

### Post by Intel520 on 2012-06-17
Hello,

The problem is that Unity and Gnome both freeze after I log in. The panels show up and I can move my mouse, but I can't click on anything. Opening Terminal by Ctrl+Alt+T doesn't work either. Unity 2D and Gnome Classic Without Effects work perfectly. I think it has something to do with my GPU drivers (AMD Radeon HD5750), and I installed Catalyst 12.4, which installed correctly by using a patch, but Unity and Gnome still didn't work. Now I installed the Ubuntu fglrx drivers, but I still got the same problem. 

If I run fglrxinfo in Terminal it prints a correct output. However, if I go to my System Details in the System Preferences, it says the graphics are VESA.

I am using Ubuntu 12.04 LTS.


Thanks in advance,
Intel520

---

### Post by Intel520 on 2012-06-18
Bump.

---

### Post by Intel520 on 2012-06-19
Bump.

---

### Post by Intel520 on 2012-06-21
Bump.

---

### Post by Intel520 on 2012-06-23
Bump.

---

### Post by jmfal on 2012-06-23
We;come to Ubuntu

Try rebooting into your grub screen and select the recovery kernal
Arrow down to:  dpkg   fix broken packages>> press enter

Follow prompts and answer question to continue >>press "y" >> press enter

If the terminal recommends manually running a command, type it in at t he command prompt and >>press enter

If you are brought back to the options menu  select resume normal boot or at the command prompt :
```
 startx    
``` 
Press enter
enter user name if asked>>press enter
enter password at prompt(you will not see it so type carefully)
You should be at the login screen>>login   and try to figure out the problem.
I would try to uninstall and reinstall the driver and see if that works
You can also try the "search this forum" tab and enter your thread title

---


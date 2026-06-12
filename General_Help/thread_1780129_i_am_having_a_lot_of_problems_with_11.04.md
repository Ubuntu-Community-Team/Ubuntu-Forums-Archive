---
title: "i am having a lot of problems with 11.04"
date: 2011-06-11
forum: General Help
---

### Post by Asto11 on 2011-06-11
After upgrading to 11.04 i tried changing some setting in compiz. Since then i am not able to do anything with my screen and keeps flickering and displaying this error message 

We are sorry, Compiz Kde event loop plugin closed unexpectedly.You can help us improve KDE software by reporting this error.

Note:its safe to close this dialog if you do not want to report this bug.

Atleast 10 of the above window opens up and the screen keeps flickering. Before i try to do anything it flickers, cannot open the terminal or do anything. Can anyone advise me on this? i am a new user

---

### Post by linuxinstalledfromhdd on 2011-06-11
> **Asto11 said:**
> After upgrading to 11.04 i tried changing some setting in compiz. Since then i am not able to do anything with my screen and keeps flickering and displaying this error message 

We are sorry, Compiz Kde event loop plugin closed unexpectedly.You can help us improve KDE software by reporting this error.

Note:its safe to close this dialog if you do not want to report this bug.

Atleast 10 of the above window opens up and the screen keeps flickering. Before i try to do anything it flickers, cannot open the terminal or do anything. Can anyone advise me on this? i am a new user

Have you tried testing your system with 10.10 to see if any of this happens?

[http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/](http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/)

---

### Post by Asto11 on 2011-06-11
i was using 10.10 and i updated to 11.04 through the update manager, i did not do any testing, i was not happy with the appearance and started doing random changes in compiz, which led to this problem, when i enabled some setting there (which i don remember ) and since then its been like this :(

---

### Post by linuxinstalledfromhdd on 2011-06-11
> **Asto11 said:**
> i was using 10.10 and i updated to 11.04 through the update manager, i did not do any testing, i was not happy with the appearance and started doing random changes in compiz, which led to this problem, when i enabled some setting there (which i don remember ) and since then its been like this :(

I'm not using 11.04. Too many issues. Too many problems. I had to reinstall 10.10:   I need my printers to work.. etc..  I understand your pain.

Here you go:

[http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/](http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/)

---

### Post by Asto11 on 2011-06-11
is there anyway to start it without compiz? i mean i need some way of disabling it before booting because i cant do anythng once it boots

---

### Post by linuxinstalledfromhdd on 2011-06-11
Go to Appearance, and Visual Effects. And should be able to turn it off. :)

---

### Post by Asto11 on 2011-06-11
cant do that , i cant do anything once it boots... i need some other way of doing it.. the screen goes crazy once i boot

---

### Post by linuxinstalledfromhdd on 2011-06-11
Ah..  You would need to boot into FailsafeX mode.  Reboot your system, and select the recovery mode right below your current kernel in Grub.    When you get to the menu eventually (it may take some time) select Failsafe mode. And then you should be back inside to disable Extra Effects in Compiz and then reboot you system. :)

---

### Post by Asto11 on 2011-06-11
i did not understand what u said, i do not know what kernel grub is :(..i am very new user

---

### Post by linuxinstalledfromhdd on 2011-06-11
Reboot your system.  At the Grub Menu (which is the one that pops up before the purple looking logo) and select the recovery kernel. It is the one just underneath the one that is selected by default in Grub.  That will take you into recovery mode..  Then select FailsafeX to boot into Ubuntu..   so you can undo the changes you want. :)

---

### Post by Asto11 on 2011-06-11
Ah i know that menu, but it is not showing up either!!

---

### Post by linuxinstalledfromhdd on 2011-06-11
No grub? 

You can wait for a grub helper if you want to wait in this group, but it is going to take some time. :)   

BUMP

---

### Post by linuxinstalledfromhdd on 2011-06-11
bump

---

### Post by cbowman57 on 2011-06-11
Hold the shift key when the system starts to boot, it should bring up the grub menu.

---

### Post by wildmanne39 on 2011-06-11
> **Asto11 said:**
> Ah i know that menu, but it is not showing up either!!
Hi, if you get the grub menu since you changed setting in compiz run this command.
```
unity --reset
```

---


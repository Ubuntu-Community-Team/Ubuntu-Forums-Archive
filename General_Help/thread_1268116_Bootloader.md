---
title: "Bootloader"
date: 2009-09-16
forum: General Help
---

### Post by CitroenLover on 2009-09-16
When powering up PC after P.O.S.T. checks Bootloader screen appears with following 8 lines :-
Ubuntu 9.04, kernal 2.6.28 - 15 - generic

then as above but after generic  (recovery mode )

Underneath these 2 lines are twin lines for 11 - 13 - 14  'generic' and '(recovery mode)

I select either number 15 OR Longhorn as I can boot into Windows Vista Home.

Not a problem but I wonder why ? :confused:

---

### Post by QIII on 2009-09-16
Generally when a new kernel is installed, the previous kernels will be left as options in your menu.lst.  It's handy to be able to go back to an older kernel if you have problems with the latest.

The reason you have pairs is that the "recovery" option takes you to ... wait for it ... system recovery utilities.

You can remove the menu.lst entries and the old kernels if you are adventurous.

---

### Post by Finalfantasykid on 2009-09-16
You can edit the menu by editing the menu.lst file...

```
gksudo gedit /etc/boot/grub/menu.lst
```

That should be it I think.  Once in there you can comment out all the kernels you no longer want.  Alternatively, I think you can also edit one of the lines near the beginning, which will say how many kernel versions you want displayed(I can't remember what the line says though).  Maybe someone else will have a more detailed answer.

---


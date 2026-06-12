---
title: "Firefox text issue in Ubuntu 10.10"
date: 2010-11-03
forum: General Help
---

### Post by aaekas on 2010-11-03
[SIZE=2]HI
I have installed Ubuntu 10.10 dual boot with Win 7.
I have come across problem in Firefox, whenever i use scroll on web page the text come messy. it looks like overlapping over each other. i have tried various things like changing the fonts, disable keyboard navigation but nothing helps. but when i try to take snapshot of page with 'prt scr' button the text becomes clear.  its frustrating.

any one has any answer?[/SIZE]:confused:

---

### Post by P4man on 2010-11-03
Sounds like an issue with your videodriver. What videocard do you have, and what (if any) drivers are you using?

---

### Post by aaekas on 2010-11-04
> **P4man said:**
> Sounds like an issue with your videodriver. What videocard do you have, and what (if any) drivers are you using?
I got nVidia basic which comes with Compaq CQ60-320SA
i didn't install any other software except what Ubuntu picked up while installing.

---

### Post by P4man on 2010-11-05
try installing the proprietary nvidia drivers. It seems you a nvidia geforce 8200 in there; you can confirm that by opening a terminal from applications | accessoiries | terminal and typing in

```
lspci
```

If that is correct,  go to system | administration | additional drivers. let it search it should prompt you for nvidia drivers. activate nvidia-current.

---


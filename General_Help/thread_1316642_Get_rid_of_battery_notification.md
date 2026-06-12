---
title: "Get rid of battery notification"
date: 2009-11-06
forum: General Help
---

### Post by Niniel on 2009-11-06
Hello,

I'm using 9.10 on an HP Pavilion laptop that is permanently plugged in and where the battery is totally worn out (about 3 % capacity left, not enough to even boot KK :) ) After installing KK, I am now seeing a notification every time I log in that the battery is badly worn. That is rather annoying and I would like to get rid of it. Any suggestions as to how to disable just the battery warning?

Thank you.

---

### Post by satnelav on 2009-11-20
Same problem.

---

### Post by emigrant on 2009-11-20
can't you right click on the notification on the panel and remove it?

---

### Post by $teve on 2009-11-20
System>Preferences>Power Management, "General" Tab. This allows you to get shot of the icon... maybe the start-up notification goes with it? ...it doesnt bother me that much so i havent tried

---

### Post by P4man on 2009-11-20
try 

```
gconf-editor
```

browse to apps > gnome-power-manager > notify

Deselect "low_capacity" (and maybe "perhaps_recall")

---


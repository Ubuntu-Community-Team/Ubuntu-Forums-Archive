---
title: "Small question about firestarter."
date: 2006-05-04
forum: General Help
---

### Post by morbid_bean on 2006-05-04
Do i have to have the fire starter window thing open at all times to keep my computer protected or when its closed dose it still protect me?

---

### Post by towsonu2003 on 2006-05-04
[QUOTE=morbid_bean]Do i have to have the fire starter window thing open at all times to keep my computer protected or when its closed dose it still protect me?[/QUOTE]
it will protect you even if you close that windows. the window is basically a gui for configurations. 

to check if firestarter is running while gui (window) is closed, in a terminal, do
```

sudo /etc/firestarter/firestarter.sh status

```

---

### Post by morbid_bean on 2006-05-04
[QUOTE=towsonu2003]it will protect you even if you close that windows. the window is basically a gui for configurations. 

to check if firestarter is running while gui (window) is closed, in a terminal, do
```

sudo /etc/firestarter/firestarter.sh status

```[/QUOTE]

Ok it worked great thanks

---

### Post by towsonu2003 on 2006-05-04
[QUOTE=morbid_bean]Ok it worked great thanks[/QUOTE]
you're welcome. just a small note I just remembered. if you change your network interface, don't forget to tell that to firestarter. 

example: 
you are using dial up (ppp0) and configure firestarter that way
you disconnect
you plug in a network cable and start using ethernet (eth0)
use firestarter (window) preferences to configure

---


---
title: "Bamboo Tablet"
date: 2010-05-15
forum: General Help
---

### Post by 5systems on 2010-05-15
Sorry if in the wrong place, but I was not sure where exactly to post this questions.  

Can I make my bamboo tablet act like a mouse instead of a pen? I am using the latest version of Ubuntu 10.4 I believe.

thanks

---

### Post by Favux on 2010-05-16
Hi 5systems,

What is your model of Bamboo?

---

### Post by 5systems on 2010-05-21
CTE-450

Thanks

---

### Post by Favux on 2010-05-21
Alright, you can try to set your stylus in relative mode instead of absolute.  You'd enter in a terminal the following xsetwacom command:
```
xsetwacom set stylus Mode Relative
```
The naming convention has been changed so in Lucid stylus will have a longer more descriptive name.  To find it enter into a terminal:
```
xinput --list
```
Then simply substitute that name with the quotes, or the ID number, for stylus in the xsetwacom command.

---

### Post by 5systems on 2010-05-29
Cool, Thanks, now how do I make it stick once I reboot?

---

### Post by dino99 on 2010-05-29
maybe: xsetwacom set stylus Mode Absolute :P

---

### Post by Favux on 2010-05-29
Hi 5systems,

You want to create a script file, call it say .xsetwacom.sh.  Then put the command in it.  Make the script file executable by right clicking on it, chose Properties and then Permissions.  Check Make executable.  Then set it up in auto-start so it runs for each Session.

---


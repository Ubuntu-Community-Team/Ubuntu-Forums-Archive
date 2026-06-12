---
title: "Can i disable/enable key repeat from a terminal?"
date: 2010-04-07
forum: General Help
---

### Post by Mr_VeRiTy on 2010-04-07
Hi, when I go on flash games I have to disable key repeat due to problem [here]("http://ubuntuforums.org/archive/index.php/t-1304066.html"), is there a command to do this from a terminal and if there is, how do I assign that command to a key, so I can easily enable/disable key repeat.

I'm using gnome and karmic koala.

---

### Post by spibou on 2010-04-07
> **Mr_VeRiTy said:**
> Hi, when I go on flash games I have to disable key repeat due to problem [here]("http://ubuntuforums.org/archive/index.php/t-1304066.html"), is there a command to do this from a terminal and if there is, how do I assign that command to a key, so I can easily enable/disable key repeat.

```
xset r off
``` turns off key repeat.```
xset r on
``` turns it on again. For related information do```
man xset
```
As for assigning the command to a key I'm not sure if it can be done but you can create functions. For example```
on () { xset r on ; }
``` will ensure that when you type **on** followed by <Enter> key repeat is turned on. You can create functions whose name contains just 1 letter.

---


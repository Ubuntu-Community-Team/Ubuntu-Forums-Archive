---
title: "changing the keyboard"
date: 2010-05-29
forum: General Help
---

### Post by Icebear on 2010-05-29
hi 

as my note is getting older I am now trying out lubuntu
My main problem is at times I need to change my keyboard layout to Russian
I found one solution by typing in terminal

setxkbmap -option grp:switch,grp:alt_shift_toggle,grp_led:scroll us,ru

which is fine but I very much prefer if I could change to the Russian phonetic keyboard rather than the standard Russian keyboard

---

### Post by simosx on 2010-05-30
> **Icebear said:**
> hi 

as my note is getting older I am now trying out lubuntu
My main problem is at times I need to change my keyboard layout to Russian
I found one solution by typing in terminal

setxkbmap -option grp:switch,grp:alt_shift_toggle,grp_led:scroll us,ru

which is fine but I very much prefer if I could change to the Russian phonetic keyboard rather than the standard Russian keyboard

You need to specify the 'phonetic' variant of the Russian keyboard layouts (if not specified, the default layout is used).

What you need to do is add the paramenter 
[INDENT]-variant ",phonetic"[/INDENT]
The purpose of the comma is to specify that for the first layout (us) you want to default (first) variant. For the second layout (ru), you want 'phonetic'.

---

### Post by Icebear on 2010-05-31
Thankyou so much simosx

you have made my life a lot easier
:popcorn:

---


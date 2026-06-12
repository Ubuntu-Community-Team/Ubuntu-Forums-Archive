---
title: "Why do Icons flicker with conky"
date: 2010-11-06
forum: General Help
---

### Post by SINNISTER on 2010-11-06
hey all

if you wondering yes i have enabled double buffering.

but for some reason my icons on my desktop disapear and can only see them if i hover my mouse over but it only lasts 2 sec then gone again until i move my mouse over it once again.

please help.

if you would like i could attach me conky config file just ask.

thanks a million

---

### Post by tristan on 2010-11-06
I had this problem too. After a bit of research and testing I found that the following .conkyrc settings fix the problem:

```
own_window yes
own_window_transparent yes
own_window_type override
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
```

---

### Post by SINNISTER on 2010-11-08
awesome i shall try it out now and report back ASAP

thanx a million

---


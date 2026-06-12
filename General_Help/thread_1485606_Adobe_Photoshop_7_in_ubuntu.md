---
title: "Adobe Photoshop 7 in ubuntu"
date: 2010-05-17
forum: General Help
---

### Post by karthick87 on 2010-05-17
I have installed Adobe Photoshop 7 in ubuntu using wine,All the tools works fine except [COLOR=Blue]cloning stamp[/COLOR][COLOR=Black].When i use cloning stamp it shows the following error "[COLOR=Red]Could not use the cloning stamp because the area to clone has not been defined(Alt-click to define a source point)[/COLOR]"[/COLOR]How to rectify this error..?

---

### Post by ssj6akshat on 2010-05-17
You need to select an area to clone from by Alt+Click

---

### Post by karthick87 on 2010-05-17
> **ssj6akshat said:**
> You need to select an area to clone from by Alt+Click

Yes i know that but after selecting the area also i get the same error..

---

### Post by mc4man on 2010-05-17
There is a conflict with compiz - move windows (alt+button1), just go into compizconfig settings manager -> window management -> move windows and change the setting (add another button or whatever to 'initiate window move'

you'll get the idea

---

### Post by karthick87 on 2010-05-17
> **mc4man said:**
> There is a conflict with compiz - move windows (alt+button1), just go into compizconfig settings manager -> window management -> move windows and change the setting (add another button or whatever to 'initiate window move'

you'll get the idea


I din understand,what you are coming to say..?

---

### Post by mc4man on 2010-05-17
If you have compiz enabled, then alt+left mouse click is set to 'move window' and won't work in photoshop as expected.

So you need to change it to something else in ccsm. If compizconfig-settings-manager isn't installed then,

```
 sudo apt-get install compizconfig-settings-manager
```

You'll find it in -> System -> Preferences or open a terminal and go
```
ccsm
```
 
Then as previously mentioned....

---

### Post by karthick87 on 2010-05-17
> **mc4man said:**
> If you have compiz enabled, then alt+left mouse click is set to 'move window' and won't work in photoshop as expected.

So you need to change it to something else in ccsm. If compizconfig-settings-manager isn't installed then,

```
 sudo apt-get install compizconfig-settings-manager
```You'll find it in -> System -> Preferences or open a terminal and go
```
ccsm
```Then as previously mentioned....

I have installed and tried but still no change..

---

### Post by karthick87 on 2010-05-18
I have used win+alt key to clone the source that worked for me..

---


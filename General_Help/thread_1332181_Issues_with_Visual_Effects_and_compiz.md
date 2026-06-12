---
title: "Issues with Visual Effects and compiz"
date: 2009-11-20
forum: General Help
---

### Post by pi4r0n on 2009-11-20
Hello ALL

Could I kindly ask you for you help please. I have installed **compiz** on my **Ubuntu Kermic** with **Radeon HD 4500 Series** installed some Windows 7 themes items (Icons, window effects etc..)

It was working perfectly fine for around 2 weeks but then something happened (Dont ask me what I dont have a clue) and now each time I logout, reboot or shut down my laptop and start system again **Visual Effects in Appearance** is selected as [COLOR="Red"]**None**[/COLOR] :( and they need to be on [COLOR="SeaGreen"]**Extra**[/COLOR].

Could someone please help me and point me info the right direction on how to automatically select Extra each time with out doing it manually.

Cheer

pi4r0n

---

### Post by emigrant on 2009-11-20
not sure whether this helps, but worth a try:
go to terminal and type
```

gconf-editor

```
desktop>gnome>interface
tick 'enable animation'

---

### Post by pi4r0n on 2009-11-20
> **emigrant said:**
> not sure whether this helps, but worth a try:
go to terminal and type
```

gconf-editor

```
desktop>gnome>interface
tick 'enable animation'

enable animation is ON (ticked already); so I still have to go to Appearance and tick Extra option in Visual Effects tab :(

---

### Post by pi4r0n on 2009-11-20
Stupid me :( in order to fix this issue I only had to add entry to **Start Application** to execute **compiz** on start.

I am such an idiot I have not spot this before :(

---


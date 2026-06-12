---
title: "compiz in 11.10"
date: 2011-10-19
forum: General Help
---

### Post by linuxaddix on 2011-10-19
okay so i went back to 11.10 and messed with it.and guess what no bugginess yet.as soon as i logged in the first time i logged right back out and went back into it and it was fine.i even installed compiz with no crashing.if you want compiz here's how to do it:
firstly go to ubuntu spftware and get synaptics
type in compiz at the search
install all you want for your compiz including fusion icon
open up compiz and go to general options/desktop size
horizontal virtual size at 4
vertical virtual size 1
number of desktops 4 or whatever your liking
get cube and rotate cube
unity uninstalls now
click unity back on and select the middle choice(sorry forgot what it was)
now log out and log back in and there you go.

---

### Post by linuxaddix on 2011-10-19
only question is how do i get the fusion icon on the panel?

---

### Post by stinkeye on 2011-11-05
If you want fusion-icon in the panel
you'll need to use dconf-editor.

dconf-editor is contained in the package dconf-tools
```
sudo apt-get install dconf-tools
```

Then run dconf-editor and navigate to 
desktop > unity > panel 

Add fusion-icon to the end of the list using the same format as the other entries.
ie insert a **comma** then a **space** followed by **'fusion-icon'**
```
, 'fusion-icon'
```
Then press enter.

---

### Post by Frogs Hair on 2011-11-05
> **linuxaddix said:**
> okay so i went back to 11.10 and messed with it.and guess what no bugginess yet.as soon as i logged in the first time i logged right back out and went back into it and it was fine.i even installed compiz with no crashing.if you want compiz here's how to do it:
firstly go to ubuntu spftware and get synaptics
type in compiz at the search
install all you want for your compiz including fusion icon
open up compiz and go to general options/desktop size
horizontal virtual size at 4
vertical virtual size 1
number of desktops 4 or whatever your liking
get cube and rotate cube
unity uninstalls now
click unity back on and select the middle choice(sorry forgot what it was)
now log out and log back in and there you go.

I used the same method , I found that disabling the Unity plug-in setting Compiz and re-enabling the plug-in worked well for me also. Paying close attention to the dialog boxes is important as well .

---


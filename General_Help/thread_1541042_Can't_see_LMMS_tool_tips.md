---
title: "Can't see LMMS tool tips"
date: 2010-07-28
forum: General Help
---

### Post by BurningSludge on 2010-07-28
[FONT=Comic Sans MS][SIZE=3]I can't see the text on Linux Multi Media Studio tool tips because the background of the tool tips are always yellow. Is there any way to force LMMS to use my default theme?[/SIZE][/FONT]

---

### Post by Trucoto on 2010-07-28
[https://bugs.launchpad.net/ubuntu/+source/lmms/+bug/561562](https://bugs.launchpad.net/ubuntu/+source/lmms/+bug/561562)

---

### Post by BurningSludge on 2010-07-28
[FONT=Comic Sans MS][SIZE=3]I went to Launch Pad already and I still don't understand how to fix the bug.[/SIZE][/FONT]

---

### Post by BurningSludge on 2010-07-30
[FONT=Comic Sans MS][SIZE=3]I changed my system's tool tip text color to gray but this will not be solved until the LMMS tool tip background can be changed.[/SIZE][/FONT]

---

### Post by tylerjwilk on 2010-11-14
**LMMS Tool Tips FIXED**

Here is a temporary FIX until LMMS is patched.

* Close LMMS
* Right click on Desktop
* Click Change Background
* Click Theme Tab
* Select Current Theme
* Click Customize
* Click Color Tab
* Set tooltip Background Color to White
* Set tooltip Font Color to Black
* Close Customize
* Close Theme
* Open LMMS

You should now have readable tooltips in LMMS

---

### Post by rhiannonr on 2011-08-04
worked like a charm! thanks!!

---

### Post by neu2buntu on 2011-08-15
I'm guessing you are using a pre 0.4.6 version of lmms as iirc this was fixed in this release so anyway open the terminal and do code ```
gksu gedit /usr/local/share/lmms/themes/default/style.css
``` and copy and paste these lines to that file and save, restart lmms 
```
QToolTip {
	border-radius: 4px;
	background: qlineargradient(spread:reflect, x1:0.5, y1:0.5, x2:0.5, y2:0, stop:0 rgba(0, 0, 0, 255), stop:1 rgba(50, 50, 50, 220));
	opacity: 175;
	border: 1.5px solid rgba(0,0,0,255);
	color: #00ff00;
}
```  probably after line 140, although it shouldnt matter.

this doesnt cover every single tooltip yet e.g the "what's this" help feature, but i will create a patch for it.

---


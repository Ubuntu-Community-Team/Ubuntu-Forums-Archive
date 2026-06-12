---
title: "my window title bars and borders keep missing"
date: 2009-08-06
forum: General Help
---

### Post by indranama on 2009-08-06
Once in about 4 hours, my ubuntu vanishes the windows title bars and borders. I have to re-login to gain them.

I think this is a problem in X, isn't it? I also use a GTK theme. (Compiz is here, but my window decorator is GTK)

this is what I have in my xorg.conf file
```
Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection
```

Can anyone help me to solve this?

---

### Post by P4man on 2009-08-07
are you using compiz ? check if you have the windows decorator plugin enabled.

While hardly a great solution, at least rather than rebooting, you can press alt F2 and enter:

```
gtk-window-decorator --replace
```

That should give you your borders back, but doesn't cure the source of the problem. Perhaps the theme you are using is buggy?

---

### Post by indranama on 2009-08-07
Here is current situation.
1. Yes I use Compiz, and "Decoration" plugggin is enabled.
2. My window decorator is GTK
3. My theme is "wild-shine", a well known Ubuntu theme.

Will this info be helpful to have a decision?


Thanks for the command to re-draw the borders :) its excellent.

---

### Post by P4man on 2009-08-07
didnt know those themes, but I just installed it and it looks gorgeous. i'll let you know if I get the same problem now :).

---


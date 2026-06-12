---
title: "How to change the frequency of the monitor"
date: 2006-06-01
forum: General Help
---

### Post by drinkingmouse on 2006-06-01
I successfully installed Ubuntu 6.06, but when I tried to change the frequency of the monitor (now is only 60Hz), there are only 50Hz and 60Hz for me to choose, can anyone tell me how to change it to 85Hz (I used to use this frequency).

On the other hand, I cannot see files/folders with chinese name, can anyone help me? 

Really thanks a lot!

---

### Post by drinkingmouse on 2006-06-01
no one willing to help?

I guess it should be the problem that Drapper cannot specify my monitor, what can I do? Thanks.

---

### Post by tom56 on 2006-06-01
I think I have a similar problem. In Gnome I can select the resolution I want 1024x768 (85khz), but my login screen seems to be at a bigger resolution, and therefore a lower frequency. The flickering is realy annoying. I know I can fix this by editing my xorg.conf but I was just wondering if there is a GUI way of doing this (because if not I can file a bug asking for it).

---

### Post by drinkingmouse on 2006-06-01
For me, even in 1024 x 768, I can only use either 56Hz or 60Hz...

Can you tell me how to fix it? Thanks a lot.

---

### Post by tom56 on 2006-06-01
Post the Screen section from your /etc/X11/xorg.conf

---

### Post by drinkingmouse on 2006-06-01
I think I should change the xorg.conf, the monitor part.
(The screen part is fine)

But I cannot change anything because I am not logged in as root.
But I think Ubuntu have no root user, isn't it?
What can I do to change the xorg.conf?

---

### Post by drinkingmouse on 2006-06-01
I think I can use root now...

Pobably I will solve the problem...

But another question is...

I cannot see the chinese file/folder names,
what can I do?

Here is part of my xorg.conf

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

THank You.

---

### Post by LKRaider on 2006-06-01
gksudo gedit /etc/X11/xorg.conf

I still don't know why there isn't a GUI for configuring this file, since out of all the configs around, it's the most common to edit.

---


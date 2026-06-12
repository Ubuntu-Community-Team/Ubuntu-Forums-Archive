---
title: "Anybody know how to kill x (restart session) in xub?"
date: 2009-07-20
forum: General Help
---

### Post by infinitelink on 2009-07-20
Hey there, 

Correcting an earlier post: anyone know how to kill x to restart the session in xubuntu? Know how to re-enable Ctrl+Alt+Backspace?

[strike]I've read Ctrl+Alt+Esc is associated with X-kill in xfce, but it doesn't work. Anybody know if Xubuntu has disabled it, and if so, how to re-enable it (I'm looking in the settings manager but can't find any setting or I just don't know what to look for).[/strike]

---

### Post by Kraut~salat on 2009-07-20
[http://www.howtogeek.com/howto/linux/disable-ctrlaltbackspace-from-restarting-x-windows-on-linux/](http://www.howtogeek.com/howto/linux/disable-ctrlaltbackspace-from-restarting-x-windows-on-linux/)

tells you how to disable it. The reverse should do the trick for you then

---

### Post by prshah on 2009-07-20
> **infinitelink said:**
>  anyone know how to kill x to restart the session in xubuntu? Know how to re-enable Ctrl+Alt+Backspace?


You can either give this terminal (Applications-Accessories-Terminal) command```
sudo dontzap --disable
``` ==OR== add/edit the following lines in your /etc/X11/xorg.conf```
Section "ServerFlags"
	Option	"DontZap"	"false"
EndSection

```

I recommend the second method because dontzap is not installed on Ubuntu systems by default; you need to apt-get it.```
sudo apt-get install dontzap
```

---


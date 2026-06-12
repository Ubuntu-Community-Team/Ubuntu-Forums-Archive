---
title: "Changing panel font colours"
date: 2010-01-11
forum: General Help
---

### Post by lukster91 on 2010-01-11
Hey,

Probably a stupid question with a simple solution... I use Ubuntu Karmic 9.10, been trying to change the font colour with regards to time/date, and the 'Applications, Places and System' buttons, along with the wireless network, battery life, volume control and the indicator applet. I have it as 100% transparent because I prefer that look and feel about it, but I can't find the controls to change the colour of the text etc on the pannel... Anyone got any ideas where the controls are? 

Thanks,

Luke

---

### Post by Grenage on 2010-01-11
I believe it's under the config file:

/home/.gtkrc-2.0

The BG and FG values (hex) can change the colours.

---

### Post by llawwehttam on 2010-01-11
U sed to use gconftool-2 to do this sort of thing. Can't remember how now. Try googleing it.

---

### Post by lukster91 on 2010-01-11
Sudo gedit /home/.gtkrc-2.0 right? 

File doesn't exist.

Isn't there a GUI way of doing it?

Or a program I can download that will do it?

---

### Post by lukster91 on 2010-01-11
> **llawwehttam said:**
> U sed to use gconftool-2 to do this sort of thing. Can't remember how now. Try googleing it.

Googled it, also tried it, I don't really understand it.

Are colours hexadecimal for gconftool-2?

---

### Post by TopEnder on 2010-01-11
G'Day,  I think you maybe after [COLOR="Blue"]Gnome Color Chooser[/COLOR] it's in Synaptic Package Manager once installed you can access it via System/Preference/Gnome Color Chooser.

---

### Post by lukster91 on 2010-01-11
> **TopEnder said:**
> G'Day,  I think you maybe after [COLOR="Blue"]Gnome Color Chooser[/COLOR] it's in Synaptic Package Manager once installed you can access it via System/Preference/Gnome Color Chooser.

Thank you very much! Much appreciated.

---


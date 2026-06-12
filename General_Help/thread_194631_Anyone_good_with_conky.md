---
title: "Anyone good with conky?"
date: 2006-06-11
forum: General Help
---

### Post by souteneur3190 on 2006-06-11
Ok I have conky the way i want it to look except its in its own winows.  I want it just to appear like gdesklets, also how will i be able to integrate this with my compiste manager (im using kwin so i can use kcontrol, just for its composite manger, but i still have gnome).

Also it says that I am unable to draw a double buffer, whats up with that?

---

### Post by Imexius on 2006-06-11
Open up .conkyrc

# Create own window instead of using desktop (required in nautilus)
own_window no

make sure own_window option is like this.

---

### Post by souteneur3190 on 2006-06-11
thanks, the only problem is the flikering (buffer stuff)

---

### Post by souteneur3190 on 2006-06-11
No one has experienced any problems like me?
In the config file I enable double buffer and in the terminal it says that cant draw double buffer swiching to single.

---

### Post by mcduck on 2006-06-12
[QUOTE=souteneur3190]No one has experienced any problems like me?
In the config file I enable double buffer and in the terminal it says that cant draw double buffer swiching to single.[/QUOTE]
have you enabled dbe in your xorg.conf? without that, there's no double buffering ;)

---

### Post by u-blunt-2 on 2006-06-17
What about the disappearing icons on the desktop ?

---


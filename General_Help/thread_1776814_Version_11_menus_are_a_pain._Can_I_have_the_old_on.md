---
title: "Version 11 menus are a pain. Can I have the old ones back?"
date: 2011-06-06
forum: General Help
---

### Post by the big e on 2011-06-06
I liked the old menu bar with the "applications" menu (which automatically sorted your applications by category) and the "administration" menu for system tools. I could find everything.

I do not see how the newfangled chiclet-buttons are an improvement and I am still trying to find my way around them. 

Any suggestions for getting a good application listing like I had before>

---

### Post by linuxinstalledfromhdd on 2011-06-06
Click on top left corner of Unity. Type in the search box for Login.  Unlock. And select from the dropdown menu Ubuntu Classic. And exit to  save. Reboot to make sure the changes have taken effect.

---

### Post by uRock on 2011-06-06
Log out and select Classic Ubuntu, then log back in.

---

### Post by the big e on 2011-06-06
Thank you! Now I'm happy.

---

### Post by the big e on 2011-10-18
Here we go again, several months later. I just upgraded to Oneiric Ocelot, and it's giving me the same chiclet-button menu interface I had before, and the old helpful tips about going back to the old menus don't work any more because they changed that part. Anyone know what to do now?

---

### Post by robert shearer on 2011-10-18
Install the package gnome-session-fallback

```
sudo apt-get install gnome-session-fallback
```

Then reboot and choose 'Gnome classic' at the login box.

---

### Post by the big e on 2011-10-18
I just installed gnome-session-fallback, as uRock and Robert Shearer both suggested. Thanks! Much Better! But wasn't there another menu called administration or something like that? I think the things in that menu have moved to Applications>Other but I am not 100% sure...

---

### Post by robert shearer on 2011-10-18
> that menu have moved to Applications>Other but I am not 100% sure... 

be sure !!  that is now how it is. :) look also in Applications>System tools>System settings for other admin configuration tools.

Note also that to customise/alter your panels you now have to **alt +** right-click to bring up the panel menus. (previously right-click only)

---


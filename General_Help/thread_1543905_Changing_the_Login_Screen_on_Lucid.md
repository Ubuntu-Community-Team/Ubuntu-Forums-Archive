---
title: "Changing the Login Screen on Lucid"
date: 2010-08-01
forum: General Help
---

### Post by PhixionalTruth on 2010-08-01
I can change the background but I have been trying to change the login itself. How do I accomplish this. Thank you.

---

### Post by sisco311 on 2010-08-01
> **PhixionalTruth said:**
> I can change the background but I have been trying to change the login itself. How do I accomplish this. Thank you.

You can change the theme/icons/cursor/fonts as well.  Add gnome-appearance-properties to GDM's auto-started applications:
```
sudo cp /usr/share/applications/gnome-appearance-properties.desktop /usr/share/gdm/autostart/LoginWindow/
```

Log out, change the theme..., log back in and remove gnome-appearance-properties from GDM's auto-stared apps:
```
sudo rm /usr/share/gdm/autostart/LoginWindow/gnome-appearance-properties.desktop
```

---

### Post by PhixionalTruth on 2010-08-01
I really appreciate the help, i was able to customize things. But I recently downloaded a login theme from [http://art.gnome.org/themes](http://art.gnome.org/themes) and now I have this folder with all these pngs and a xml file. in my home folder. Now what!?!?! I can not figure it out!

---


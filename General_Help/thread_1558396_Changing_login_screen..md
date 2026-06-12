---
title: "Changing login screen."
date: 2010-08-22
forum: General Help
---

### Post by OpressedCalamity on 2010-08-22
Hello,
How would I change the wallpaper on the login screen to something else?
Thanks. :D

---

### Post by sisco311 on 2010-08-22
Add gnome-appearance-properties to GDM's autostart directory:
```
sudo ln -s /usr/share/applications/gnome-appearance-properties.desktop /usr/share/gdm/autostart/LoginWindow/
```

Log out. The appearance properties window should show up on the GDM screen. 

Configure GDM how you want, then close the window and log back in. 

When you're done and want the window to stop opening with GDM, run:

```
sudo unlink /usr/share/gdm/autostart/LoginWindow/gnome-appearance-properties.desktop
```

---

### Post by OpressedCalamity on 2010-08-22
Alright, i'll try that, thanks.

---

### Post by 0x656b694d on 2010-08-29
a bit simpler way here, which i believe does the same.

This is how to get the current wallpaper:
```

sudo -u gdm gconftool-2 -g /desktop/gnome/background/picture_filename

```
And this is how to set the new one:
```

sudo -u gdm gconftool-2 -s /desktop/gnome/background/picture_filename <filename> --type string

```
<filename> &#8212; the full path to the new wallpaper, must be accessible for reading by at least gdm user, i guess.
That worked for me.

---


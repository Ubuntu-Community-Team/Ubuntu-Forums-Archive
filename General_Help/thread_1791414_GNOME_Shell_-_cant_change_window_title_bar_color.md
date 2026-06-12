---
title: "GNOME Shell - cant change window title bar color"
date: 2011-06-26
forum: General Help
---

### Post by u-noob-tu on 2011-06-26
like the title says, i cant change the color of window title bars in GNOME shell. Its an ugly bright orange, and i tried using gnome tweak tool to change the theme, but it only changes the controls and entry boxes, it never changes the color, and its driving me nuts. any ideas?

---

### Post by nzjethro on 2011-06-26
Depending on what theme you are using, your window borders may be aligned to your theme colours. If you go to System > Preferences > Appearance, and change theme, do the title bars change? Also, you should be able to change the theme colour by selecting Customise Theme, and choosing your desired colour scheme. Some themes (I can't remember any examples, I now use Xfce, but maybe one with little boxes on the title bar) change title bar colour to match your "Selected Items" colour. Try this too.

---

### Post by cbowman57 on 2011-06-26
Did you install gnome-shell-extensions-user-theme?

Have no idea why they are orange though, that's something I haven't encountered yet.

---

### Post by nzjethro on 2011-06-27
> **cbowman57 said:**
> 
Have no idea why they are orange though, that's something I haven't encountered yet.

The default theme in Ubuntu is "Ambiance", which has (hideous IMO) bright orange as its primary colour.

If the OP hasn't customised theme, the orange may still be the default colour.

---

### Post by u-noob-tu on 2011-06-27
Got the title bar color to change, finally. Strangely, the theme I wanted (clearlooks) wouldnt work, yet when I changed to the default adwaita theme, I got the clearlooks color scheme. Not sure why that is.

---

### Post by nzjethro on 2011-06-28
> **u-noob-tu said:**
> Got the title bar color to change, finally. Strangely, the theme I wanted (clearlooks) wouldnt work, yet when I changed to the default adwaita theme, I got the clearlooks color scheme. Not sure why that is.

Strange. Well, glad you got your problem fixed.

---

### Post by nilarimogard on 2011-06-28
You can change the theme (both the GTK and titlebar - Mutter/Metacity theme) using GNOME Tweak Tool - it's available in the Ubuntu 11.10 repos and you can install using the command below:
```
sudo apt-get install gnome-tweak-tool
```

---


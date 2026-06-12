---
title: "How to make Ubuntu panels fully transparent"
date: 2010-08-20
forum: General Help
---

### Post by LewisDre4m on 2010-08-20
I found out how to make the panels fully transparent so I thought I would share it with others.

When you set the panel to be transparent in the default Ambiance theme in Ubuntu 10.04, you will find that some panel items' backgrounds are not transparent, but you can make them transparent and consistent with others, following these steps:

Go to Applications (or Main Menu) > Accessories > Terminal.
Enter cp -R /usr/share/themes/Ambiance ~/.themes/
Enter gedit ~/.themes/Ambiance/gtk-2.0/gtkrc to open Ambiance's ftkrc file with gedit.
Search for this line bg_pixmap[NORMAL] = "panel_bg.png"
Comment out the line by placing a # at the beginning of the line, like this: #   bg_pixmap[NORMAL] = "panel_bg.png"
Save the gtkrc file.
Go to System > Preferences > Appearance, switch to the other theme and then back to the Ambiance theme.

Hope that helps some people

---

### Post by beercz on 2010-08-22
> **LewisDre4m said:**
> I found out how to make the panels fully transparent so I thought I would share it with others.

When you set the panel to be transparent in the default Ambiance theme in Ubuntu 10.04, you will find that some panel items' backgrounds are not transparent, but you can make them transparent and consistent with others, following these steps:

Go to Applications (or Main Menu) > Accessories > Terminal.
Enter cp -R /usr/share/themes/Ambiance ~/.themes/
Enter gedit ~/.themes/Ambiance/gtk-2.0/gtkrc to open Ambiance's ftkrc file with gedit.
Search for this line bg_pixmap[NORMAL] = "panel_bg.png"
Comment out the line by placing a # at the beginning of the line, like this: #   bg_pixmap[NORMAL] = "panel_bg.png"
Save the gtkrc file.
Go to System > Preferences > Appearance, switch to the other theme and then back to the Ambiance theme.

Hope that helps some people
Thanks for the tip - I often make my panels transparent.

---

### Post by hotrodder on 2010-08-22
*

---

### Post by Forgotten Path on 2010-08-22
Hmm... Didn't work for me, even after switching theme, logging out, and editing the original file (in /usr). Any tips?

---

### Post by LorDVipeR on 2011-01-19
I this tip don't work for me... i can't find this line [COLOR=blue]bg_pixmap[NORMAL] =  “panel_bg.png"...

gedit ~/.themes/Ambiance/gtk-2.0/gtkrc


thnks
[/COLOR]

---

### Post by stinkeye on 2011-01-19
Some themes include a panel.rc file.
In this case the actual file you want to edit is **gnome-panel.rc **

If you copied your theme to ~/.themes
To edit enter in terminal
```
gedit ~/.themes/Ambiance/gtk-2.0/apps/gnome-panel.rc
```


Line #10
```
bg_pixmap[NORMAL] = "img/panel.png"
```


If you haven"t copied the theme over to your home folder (which is not necessary)
edit the file with...
```
gksudo gedit /usr/share/themes/Ambiance/gtk-2.0/apps/gnome-panel.rc
```

---

### Post by Kexolino on 2011-02-06
Can this only be done with Ambiance?

---

### Post by stinkeye on 2011-02-06
Same method for all themes.
Check in ~/.themes first for your theme.

If your theme is installed in **/usr/share/themes**
enter in terminal 
```
gksudo nautilus /usr/share/themes
```
and edit the appropriate gtkrc or panelrc.
The line may not be exactly the same but your looking for something similar to...
```
bg_pixmap[NORMAL] = "img/panel.png
or
bg_pixmap[NORMAL] = &#8220;panel_bg.png"
```
Search for "panel".



When editing make a backup of the file first.
I do this by simply copying and pasting the file in the same diectory
which will give you a **gtkrc(copy)** file.
Then to revert back you delete the **gtkrc** file and rename **gtkrc(copy)** to **gtkrc**

---

### Post by dBuster on 2011-02-06
Is this in reference to the panels at say the top and bottom of the screen?

If so I can right click on my panels and go to properties and I can set the transparency there.  Without the need of editing any files.

Not sure if this feature is available with releases higher than 9.04 but I do not see why they would break this ability...

---

### Post by stinkeye on 2011-02-06
> **dBuster said:**
> Is this in reference to the panels at say the top and bottom of the screen?

If so I can right click on my panels and go to properties and I can set the transparency there.  Without the need of editing any files.

Not sure if this feature is available with releases higher than 9.04 but I do not see why they would break this ability...

Yep, your right, that's how you make your panel transparent but for a lot of themes the applets will still use the background image due to the 
setting in the gtkrc file.

---

### Post by Kexolino on 2011-02-06
> **dBuster said:**
> Is this in reference to the panels at say the top and bottom of the screen?

If so I can right click on my panels and go to properties and I can set the transparency there.  Without the need of editing any files.

Not sure if this feature is available with releases higher than 9.04 but I do not see why they would break this ability...

You can do that, but it only makes the panel's center (where there are no icons or menus) transparent, at least in 10.10.

---


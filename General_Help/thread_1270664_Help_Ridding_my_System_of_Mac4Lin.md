---
title: "Help Ridding my System of Mac4Lin"
date: 2009-09-19
forum: General Help
---

### Post by Joseph Schwenker on 2009-09-19
Hello everyone!  I recently tried out Mac4Lin customization pack for Ubuntu 9.04, and decided to change it back.  I was able to run the uninstall script successfully, but after restarting my computer, I noticed that all of the buttons on dialogs:

Do you want to destroy your computer, then have the entire planet earth sucked into a big hole in the center of the galaxy like a pinhead in a bathtub without a plug while all of your friends turn against you?

-------------------------------No----------------Yes

Had not been changed back to the humongous ugly ones with the big icons on them.  See for yourself here: [http://lh5.ggpht.com/_Ed2WX_IXHtg/SrWMmomVifI/AAAAAAAABRk/BpnNuyAbfxg/Screenshot-Appearance%20Preferences.png](http://lh5.ggpht.com/_Ed2WX_IXHtg/SrWMmomVifI/AAAAAAAABRk/BpnNuyAbfxg/Screenshot-Appearance%20Preferences.png)
This is as opposed to this: [http://i.zdnet.com/blogs/ubuntu-update-manager-restart-required.png](http://i.zdnet.com/blogs/ubuntu-update-manager-restart-required.png)

Does anyone know how I can restore the buttons to their former glory, without *shutters* creating a new user account?  Thanks!

---

### Post by Tipped OuT on 2009-09-19
The only thing I notice that looks wrong is, there is no icon in the little boxes that say "Close", "Open", "Help", etc.

I believe you can change this in *System< Preferences< Appearance*, in the "interface" tab.

---

### Post by Joseph Schwenker on 2009-09-19
> **Tipped OuT said:**
> The only thing I notice that looks wrong is, there is no icon in the little boxes that say "Close", "Open", "Help", etc.

I believe you can change this in *System< Preferences< Appearance*, in the "interface" tab.

The only options available in the interface tab are, "Show Icons in Menus", "Editable menu shortcut keys", and "Toolbar button labels: Icons only/Text below/beside/etc".  
If you meant the Theme tab, then I have Human chosen for my controls.

---

### Post by Tipped OuT on 2009-09-19
> **Joseph Schwenker said:**
> The only options available in the interface tab are, "Show Icons in Menus", "Editable menu shortcut keys", and "Toolbar button labels: Icons only/Text below/beside/etc".  
If you meant the Theme tab, then I have Human chosen for my controls.

Oh, well there's suppose to be an option to enable icons in the boxes or just plain text.

Try configuration editor. ```
 sudo gconf-editor 
```

Then in configuration editor, go to apps< desktop< gnome< interface<

Then scroll down through the options until you find the option to enable icons in menus.

---

### Post by Joseph Schwenker on 2009-09-19
> **Tipped OuT said:**
> Oh, well there's suppose to be an option to enable icons in the boxes or just plain text.

Try configuration editor. ```
 sudo gconf-editor 
```

Then in configuration editor, go to apps< desktop< gnome< interface<

Then scroll down through the options until you find the option to enable icons in menus.

Yay!  Thanks a bunch!  :D

---


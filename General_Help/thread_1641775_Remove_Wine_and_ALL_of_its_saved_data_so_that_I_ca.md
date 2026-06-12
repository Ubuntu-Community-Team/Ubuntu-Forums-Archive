---
title: "Remove Wine and ALL of its saved data so that I can do a &quot;fresh insall&quot;"
date: 2010-12-09
forum: General Help
---

### Post by 0949er on 2010-12-09
Hey guys, I was messing around with my seeing in wine last night and to make the long story short I broke MS Office. I have tried reinstalling (errors in installer) and even tried manually removing everything but I still get hte same errors. Now everythign worked WITHOUT A DOUBT until I started messign with setting. I want to delete wine and reinstall it.... only I want to make sure EVERYTHING settings wise is remove with it as well (does that mean I just delete the "~/.wine" folder? Is that it? Any input would be greatly appreciated!

Oh and this is a really stupid question, but how should I install it? through the "ubuntu software center" or through the command line?

---

### Post by Irony on 2010-12-09
Just delete (or rename for a backup) the ~/.wine folder (no need to reinstall) - when you then start up wine a fresh ~/.wine folder will be created.

---

### Post by bob-linux-user on 2010-12-09
I would try deinstalling via the ubuntu software centre. You will find information relating to windows programs you installed in wine in

/home/yourname/.config/menus/applications-merged
/home/yourname/.local/share/applications/wine/Programs 
/home/yourname/.local/share/desktop-directories
/home/yourname/.local/share/icons 
/home/yourname/.wine/drive_c/users/yourname/Start Menu/Programs
/home/yourname/.wine/drive_c/Program Files

so you might want to have a look in those directories as well.

MS Office 2003 and earlier should run ok in Wine.

---

### Post by Alxl on 2010-12-09
Applications | Wine | Uninstall Wine Software

---

### Post by bodhi.zazen on 2010-12-09
Uninstalling and reinstalling wine will not help. You need to remove ~/.wine and re-install as previous posters have instructed.

---

### Post by 0949er on 2010-12-09
thanks guys! I didn't even reinstall wine... I just removed my .wine directory and re-ran wine and it auto-configured a whole new system. neat!

This is what I followed from the official wineHQ website:

**5.2. How do I uninstall *all* Windows applications?**

 To remove **all programs installed under Wine**, remove the wineprefix (usually the ~/.wine directory) by pasting the following command into a terminal: 

```

rm -rf $HOME/.wine

```

But  that doesn't remove them from the system menu; to clean out the menus,  carefully paste the following commands into a terminal: 

```

rm -f $HOME/.config/menus/applications-merged/wine*
rm -rf $HOME/.local/share/applications/wine
rm -f $HOME/.local/share/desktop-directories/wine*
rm -f $HOME/.local/share/icons/????_*.{xpm,png}
rm -f $HOME/.local/share/icons/*-x-wine-*.{xpm,png}

```

---

### Post by bodhi.zazen on 2010-12-09
> **0949er said:**
> thanks guys! I didn't even reinstall wine... I just removed my .wine directory and re-ran wine and it auto-configured a whole new system. neat!

This is what I followed from the official wineHQ website:

**5.2. How do I uninstall *all* Windows applications?**

 To remove **all programs installed under Wine**, remove the wineprefix (usually the ~/.wine directory) by pasting the following command into a terminal: 

```

rm -rf $HOME/.wine

```

But  that doesn't remove them from the system menu; to clean out the menus,  carefully paste the following commands into a terminal: 

```

rm -f $HOME/.config/menus/applications-merged/wine*
rm -rf $HOME/.local/share/applications/wine
rm -f $HOME/.local/share/desktop-directories/wine*
rm -f $HOME/.local/share/icons/????_*.{xpm,png}
rm -f $HOME/.local/share/icons/*-x-wine-*.{xpm,png}

```

thank you for the detailed post, it will help others who hit this with a search =)

---


---
title: "Ubuntu 11.10 - top panel and app fonts problems after upgrade"
date: 2011-10-19
forum: General Help
---

### Post by vanameister on 2011-10-19
I upgraded to 11.10 and now my application fonts and top panel fonts/icons are ugly (antialiazing changed, font size changed, wrong theme (no way to reinforce Ambiance), wrong icons, etc.). I have not managed a way to modify my applications menu fonts and top panel theme. :(

I am using Unity/Compiz. 

Where/how can I set the antialiazing of menu/top panel fonts and modify top panel theme in compiz? 

1. System>Appearance>Theme does not have a place to modify system fonts anymore (why?). Changing the theme there does not have any effect.
2. CCSM does not seem to have a option to change system/top panel fonts. 
3. I have reseted compiz with ```
gconftool-2 --recursive-unset /apps/compiz
``` command (also for compiz1 folder). No effect.
4. I have reseted unity with ```
unity --reset
``` command. No effect.
5. I have removed configuration folders in my home directory with ```
rm -rf .gnome .gnome2 .gconf .gconf2 .metacity
``` command. No effect.
6. I have deleted ~/.themes folder. No effect.
7. It can not be a video card issue. Everything was ok under 11.04. The command ```
sudo /usr/lib/nux/unity_support_test -p
``` says that Unity Supported = Yes.

More importantly:
a) the fonts and top panel theme is OK, when another user is logged into computer with Unity/compiz (but I don't have a clue, how to copy her compiz top panel & system font settings to my settings).
b) I installed Gnome3 as an alternative and I don't have such issues with font antialiazing. But I don't want to go for Gnome3, as it seems slower and the search facility freezes my system. 

What else can be done? Can I delete/amend those settings manually? Where are the settings for top panel/system fonts stored?

:(

---

### Post by vanameister on 2011-10-23
bump

---

### Post by dathrien on 2011-10-23
Well, I have the same problem.:( 
I would be grateful for any suggestions!

---

### Post by hughh on 2011-11-30
Ditto

---

### Post by SwedishWings on 2011-12-16
Same here, the panel looks very ugly on my MBP 5,1. I think it's the anti-aliasing that fails.

/Mike

---


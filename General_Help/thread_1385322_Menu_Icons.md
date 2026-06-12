---
title: "Menu Icons"
date: 2010-01-19
forum: General Help
---

### Post by paulshepherd on 2010-01-19
Hi there. 
Fairly new Ubuntu user, so be gentle. =P

Basically, I'm trying to get rid of the menu icons (via System > Appearance > Interface), but keep there start-here icon to the left of the Applications menu title. 

Any ideas on how I could do this, without just replacing all the menu icons with 1x1 transparent files?

Thanks in advance. =]

---

### Post by fsando on 2010-01-23
> **paulshepherd said:**
> Hi there. 
Fairly new Ubuntu user, so be gentle. =P

Basically, I'm trying to get rid of the menu icons (via System > Appearance > Interface), but keep there start-here icon to the left of the Applications menu title. 

Any ideas on how I could do this, without just replacing all the menu icons with 1x1 transparent files?

Thanks in advance. =]

Basically you can't. But you could create an icon that is a blank *.png image. The space used by that icon will still be there just without icon.

To find out where you icons are, go to 

System > Preferences > Appearance

Click 'Customize', click the 'icon' tab and see which icon-theme is used. The theme name will correspond to a folder name in

/usr/share/icons/

Here you'll find a set of folders named like this:
8x8
16x16
22x22
...
etc. indicating the size of icons. Look for the subfolder 'places' and look here for the file 'start-here.png'

Most likely it's the 22x22/places or 24x24/places folder your icon is taken from. This depends upon how the theme is designed.

If you want to minimize the visuals - you could add the 'Main menu' to you panel instead of the default 'Menu bar'.

Right click on the panel chose 'Add to panel'

---


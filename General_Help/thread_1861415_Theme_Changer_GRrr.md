---
title: "Theme Changer GRrr"
date: 2011-10-15
forum: General Help
---

### Post by spiritech on 2011-10-15
HI

is there a good theme changer for ubuntu 11.10. i am using gtk-chtheme at the moment. it is good. though it does not have the choice to change the window borders, it also fails to find all the theme's in my theme folder nor does it have the option to change the icon set.. i also have Advance Settings installed, it works to a certain degree, but it fails to find hardly any of the theme's i have downloaded myself. i really feel that this area of Ubuntu is a big let down. it would be nice to have a standalone application that controls window borders, buttons and icons. as i have failed to find one yet.

---

### Post by fragos on 2011-10-15
In the software center do a search for "gnome-tweak" and install the "Advanced Settings" package. This will give you access to change some of what you want. Changing colors at this time requires editing configuration files in /usr/share/themes.

---

### Post by spiritech on 2011-10-15
> **fragos said:**
> In the software center do a search for "gnome-tweak" and install the "Advanced Settings" package. 

i already have the Gnome-tweak installed. the problem is my themes are not showing up under the GTK+ theme tab.

---

### Post by spiritech on 2011-10-15
here is a screenshot.

---

### Post by spiritech on 2011-10-15
.

---

### Post by fragos on 2011-10-16
Same here. Perhaps if a deb package theme is installed now it will show up. The 11.10 upgrade didn't pick up the ones I already had. It could also be that older gnome themes aren't compatible. Really don't have a good answer yet. I did succeed in editing the config files for Ambiance to change colors and to use a set of blue close icons I made to get rid of that horrible orange. I also used the Faenza icons and now have a theme that makes me happy.

---

### Post by mcduck on 2011-10-16
Are you sure all the themes you are trying to use are GTK3 themes? Any old themes you might have left from previous Ubuntu versions would be GTK2 themes...

Gnome-Tweak-Tool really is the best tool for the purpose, at least at the moment, and should pick any compatible themes without any problems.

---

### Post by spiritech on 2011-10-16
> Are you sure all the themes you are trying to use are GTK3 themes? Any  old themes you might have left from previous Ubuntu versions would be  GTK2 themes...

the GTK themes were Downloaded from Gnome Art. so maybe they are old themes. i am very surprised that the themes are not backward compatible. the window borders and icons still work though.

> Gnome-Tweak-Tool really is the best tool for the purpose, at least at  the moment, and should pick any compatible themes without any problems.

yes the Gnome-Tweak-Tool does does have all the options and i am surprised its not included as a default package. it does fail to have a link to compatible themes, as does the theme changer under the appearance settings.

> I did succeed in editing the config files for Ambiance to change colors  and to use a set of blue close icons I made to get rid of that horrible  orange

Thats good. Gnome Color Chooser is a good tool for changing color schemes. it lack the ability to make the changes permanent or create as new theme.

---


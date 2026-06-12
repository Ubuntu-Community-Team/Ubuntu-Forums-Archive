---
title: "editing metacity.xml for the radiance theme"
date: 2010-04-30
forum: General Help
---

### Post by Ultra_Man on 2010-04-30
I just want the radiance theme to have to title in the middle, how do I do it?

---

### Post by sisco311 on 2010-05-01
In the <!-- Window Title --> section replace x="10" with x="((3 `max` (width-title_width)) / 2)", x="9" with x="((3 `max` (width-title_width)) / 2)-1" and x="11" with x="((3 `max` (width-title_width)) / 2)+1".

run:
```
mkdir -p ~/.themes/Radiance-center/metacity-1
```
```
sed -e 's/Name=Radiance/Name=Radiance-center/' -e 's/MetacityTheme=Radiance/MetacityTheme=Radiance-center/' /usr/share/themes/Radiance/index.theme > ~/.themes/Radiance-center/index.theme
```
```
cp /usr/share/themes/Radiance/metacity-1/* ~/.themes/Radiance-center/metacity-1/
```
and
```
sed -i -e 's/x=\"9\"/x=\"((3 \`max\` (width-title_width)) \/ 2)-1\"/' -e 's/x=\"10\"/x=\"((3 \`max\` (width-title_width)) \/ 2)\"/' -e 's/x=\"11\"/x=\"((3 \`max\` (width-title_width)) \/ 2)+1\"/' ~/.themes/Radiance-center/metacity-1/metacity-theme-1.xml
```
then go to System -> Preferences -> Appearance and select the Radiance-center theme.

---

### Post by Ultra_Man on 2010-05-01
Thanks.

Also, anyone know how to prevent gnome-shell from moving the buttons to the right?

EDIT: Nevermind, I found where it is in gconf.

---


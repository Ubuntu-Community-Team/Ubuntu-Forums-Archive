---
title: "Double Applications launch-icon vs no launch-icon..."
date: 2009-09-15
forum: General Help
---

### Post by neocortex on 2009-09-15
Hello ALL!
This is, I believe, minor thing, but it anyones me to be honest. In brief, I have no Eye of GNOME launch-icon in Applications > Graphics. At the same time, Brasero launch-icon lives both in Applications > Accessories and Applications > Sound & Video.
So, how can I add EOG in Graphics and remove Brasero from Accessories?
Previously, I could manipulate with this kind of "appearance" by editing apropriate *.desktop file in /usr/share/applications/ directory. Now, this does not affect anything.
In addition, why there are duplicate *.desktop files in /usr/share/applications/ and /usr/share/app-install/desktop/? I have a theory, but do not want to play smart, being far from sure.

Thanks in advance! Best,
PM

---

### Post by VCoolio on 2009-09-15
Right click the menu icon and then "edit menu" and mess around (or run 'alacarte', which is the same application). Or open the .desktop files in a text editor (you can copy them to ~/.local/share/applications for your user, so you won't need root permission) and edit (or add) the line beginning with "Categories=". Add the menu category where you want the launcher to show up, eg. Network or Application or Graphics. Use ";" (without spaces) for multiple categories.

---


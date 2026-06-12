---
title: "Changing Button Text Color"
date: 2011-10-29
forum: General Help
---

### Post by divergex on 2011-10-29
Can anyone tell me how to change the color of the text in UI buttons? I have tried editing the css files, and in Gnome Color Chooser the button options are greyed out. I just want to change from the grey text color to black.

---

### Post by vasa1 on 2011-10-29
> **divergex said:**
> Can anyone tell me how to change the color of the text in UI buttons? I have tried editing the css files, and in Gnome Color Chooser the button options are greyed out. I just want to change from the grey text color to black.

Can you try this (after backing up the original):
Edit /usr/share/themes/XXXX/gtk-3.0/settings.ini and change **fg_color:#4c4c4c** to **fg_color:#000000**

XXXX is the name of your theme.

You may have to log out and log in again to see the changes

---

### Post by divergex on 2011-10-29
Worked great. Thanks!

---

### Post by vasa1 on 2011-10-29
> **divergex said:**
> Worked great. Thanks!

Nice to know that! I hope they sort things out before the LTS and give us a nice GUI so that people with accessibility issues don't feel left out.

---


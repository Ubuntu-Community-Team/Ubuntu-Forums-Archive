---
title: "Creating my own livecd.. need help!"
date: 2006-06-29
forum: General Help
---

### Post by mhancoc7 on 2006-06-29
Ok, I have read the wiki how to on creating my own livecd and I am ready to go. The only thing that I don't understand is when I am doing my customizations. I want to make changes to the default GDM and the look of the gnome desktop such as theme and using a custom Main Menu icon. I know how to do all those things from within my desktop. I am just not sure how I can do those things via the command line when customizing a livecd. Could someone help me with this.

Here is the wiki how to:
[https://help.ubuntu.com/community/LiveCDCustomization/Dapper]("https://help.ubuntu.com/community/LiveCDCustomization/Dapper")

Thanks in advance, Jereme

---

### Post by mhancoc7 on 2006-06-30
bump

---

### Post by xtacocorex on 2006-06-30
I have some ideas, but I'm not fully sure if they work because I've never tried this.

For GDM:
Copy your theme to /usr/share/gdm/themes
To set yours as default, change the following line in /etc/gdm/gdm.conf
```
GraphicalTheme=Human
```
set the theme name to yours

I can't seem to figure out where in the system, the default themes are set and the icon for the gnome-panel.

At least you can test the live cd you create with qemu to see if the customizations work. 

Hope this helps some.

---


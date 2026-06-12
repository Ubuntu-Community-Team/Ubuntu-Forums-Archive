---
title: "GDM Theme/Font size?"
date: 2011-05-26
forum: General Help
---

### Post by izzygalvez on 2011-05-26
I want to change my login screen (GDM) theme and font size on Xubuntu 11.04, but I have not been able to find out how to do so.

When I was using Ubuntu 10.10, ```
sudo cp /usr/share/applications/gnome-appearance-properties.desktop /usr/share/gdm/autostart/LoginWindow
``` and ```
sudo unlink /usr/share/gdm/autostart/LoginWindow/gnome-appearance-properties.desktop.
``` got the job done.

Is there a way to do this in Xubuntu?

---

### Post by hhh on 2011-05-27
Assuming Xubuntu is still using GDM (I'm currently on Debian)...

The Login-Window Manager will let you change themes. It should be in either Settings>>Login Window or System>>Login Window, or just run in a terminal...```
gksu /usr/sbin/gdmsetup
``` ... then go to the Local tab.

I don't know of an easy way to change the font, but you could try going to /usr/share/gdm/themes/[YOUR_THEME], backup the .xml file, then create a new one based on the old one and change fonts there.

---

### Post by izzygalvez on 2011-05-27
**/usr/sbin/gdmsetup** is not installed with Xubuntu 11.04.

'gdmsetup' or 'gdm-setup' is not even in the repositories. :(

---

### Post by Toz on 2011-05-27
You can try GDM Tweaker ([http://www.webupd8.org/2011/05/change-gdm-theme-background-in-ubuntu.html](http://www.webupd8.org/2011/05/change-gdm-theme-background-in-ubuntu.html)). Not sure how you would change font size though.

---

### Post by izzygalvez on 2011-05-27
**GDM Tweaker** was able to change my login theme and icons. Thanks for the tip!

I'm still stuck on figuring out how to change the fonts, though.

Attached is a screenshot of my **usr/share/gdm** folder.

---

### Post by hhh on 2011-05-27
Sorry izzy, I guess I can't help as Xubuntu's file structure is different from Debian's. I've tried to get Xubuntu 11.04 to boot from USB but neither Unetbootin nor dd seem to work.

You could try searching /usr for your theme name using Catfish or the backend of your choice.

---

### Post by Toz on 2011-05-27
> **izzygalvez said:**
> I'm still stuck on figuring out how to change the fonts, though.

Been doing some research. Maybe something here can help?

Using gconftool-2: [http://ubuntu-tutorials.com/2008/01/10/gconftool-2-gconf-editor-from-the-shell/](http://ubuntu-tutorials.com/2008/01/10/gconftool-2-gconf-editor-from-the-shell/)

Using gconftool-2 in gdm's profile: [http://ubuntuforums.org/showpost.php?p=9276779&postcount=23](http://ubuntuforums.org/showpost.php?p=9276779&postcount=23)

---


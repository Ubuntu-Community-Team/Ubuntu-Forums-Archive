---
title: "Gdm in Ubuntu 10.04"
date: 2010-07-14
forum: General Help
---

### Post by ccarmichael on 2010-07-14
Idk if they call it that anymore or not...But I went the route to install the theme by the pop up box before you log in. Well Im using a theme I made and i noticed something i wanted to change....But I can't for the life of me figure out where they are installed to to delete them so it can remake directory.

I have deleted out of .themes in home directory and themes in usr/share/themes.

Can anybody help me....Why is the theme still there?

---

### Post by cariboo on 2010-07-14
There isn't a way to change the GDM them yet, once gdm2setup is finished you should be able to change it.

---

### Post by sisco311 on 2010-07-14
> **cariboo907 said:**
> There isn't a way to change the GDM them yet, once gdm2setup is finished you should be able to change it.

GDM uses GTK themes. Changing the theme is relatively easy. :)


Add gnome-appearance-properties to GDM's autostarted applications:
```
sudo cp /usr/share/applications/gnome-appearance-properties.desktop /usr/share/gdm/autostart/LoginWindow/
```

Log out. 

Select a new theme/wallpaper/font. 

Log in and remove gnome-appearance-properties from GDM's autostarted applications:
```
sudo rm /usr/share/gdm/autostart/LoginWindow/gnome-appearance-properties.desktop
```

@OP

Check out /var/lib/gdm/.themes. /var/lib/gdm/ is the home directory of the user gdm.

---

### Post by ccarmichael on 2010-07-14
Thank you!! Thats what I was looking for was home directory of gdm (I'm great at wording things aren't I?)

You are amazing!

---

### Post by sisco311 on 2010-07-14
You're welcome!


Please mark this thread as [SOLVED].

At the top of the page, click the "[COLOR="Red"]Thread Tools[/COLOR]" Menu and then "Mark this thread as Solved".

Thanks.


P.S. Welcome to the forums!

---


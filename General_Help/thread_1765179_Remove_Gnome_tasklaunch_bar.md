---
title: "Remove Gnome task/launch bar"
date: 2011-05-22
forum: General Help
---

### Post by Elentir on 2011-05-22
I have perhaps a very strange question. I want to remove the Gnome task bar for specific users. I just want to have some icons on the desktop and that's it. I will use a pre-Unity Ubuntu, probably 8.10. Would this be possible?

---

### Post by linuxinstalledfromhdd on 2011-05-22
I would think so. I've built a nice one like this:

[http://jacob.steelsmith.org/category/section/ubuntu-kiosk-edition](http://jacob.steelsmith.org/category/section/ubuntu-kiosk-edition)

---

### Post by wojox on 2011-05-22
8.10 is EOL as far as your request yes look here [GNOME Desktop System Administration Guide]("http://library.gnome.org/admin/system-admin-guide/2.32/")

---

### Post by Purplerob on 2011-05-22
Just log in using the *User Defined Session *session on the login screen.

Or you could kill the panel using 
```
killall gnome panel
```

To bring the panel back easily make a launcher for
```
gnome-panel
```
and double click it.

---

### Post by Elentir on 2011-05-22
I'm always amazed about the speed of the replies. Thanks very much :)

---

### Post by WML Cloud on 2011-05-28
> **Elentir said:**
> I have perhaps a very strange question. I want to remove the Gnome task bar for specific users. I just want to have some icons on the desktop and that's it. I will use a pre-Unity Ubuntu, probably 8.10. Would this be possible?
This should answer all your questions regarding deleting, saving and restoring the Gnome Panel.
[http://www.wmlcloud.com/linux/how-to-save-and-restore-ubuntu-gnome-panel/](http://www.wmlcloud.com/linux/how-to-save-and-restore-ubuntu-gnome-panel/)

---


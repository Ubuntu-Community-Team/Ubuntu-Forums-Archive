---
title: "Reset theme"
date: 2010-06-14
forum: General Help
---

### Post by COKEDUDE on 2010-06-14
[http://linuxfud.wordpress.com/2007/02/14/how-to-reset-ubuntugnome-settings-to-defaults-without-re-installing/](http://linuxfud.wordpress.com/2007/02/14/how-to-reset-ubuntugnome-settings-to-defaults-without-re-installing/)
> If you don’t have access to your graphical (GUI) desktop to delete these folders in Nautilus or you’re stuck at the login screen, drop to a terminal by hitting CTRL + ALT + F1, login to your account, and run this command:

    rm -rf .gnome .gnome2 .gconf .gconfd .metacity

Get back to your GUI desktop by hitting CTRL + ALT + F7.

Login and VOILÀ! Just like the first time you ever logged into your Gnome desktop.

I discovered the method of resetting your theme above doesn't always work. 

Try this command below if you want to reset your theme. I had to restart my computer after I did this. 
```
metacity --replace 
```
[https://help.ubuntu.com/community/Metacity](https://help.ubuntu.com/community/Metacity)

---


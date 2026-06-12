---
title: "Help! Lost the panel widget for network selecting"
date: 2009-09-11
forum: General Help
---

### Post by juicyoner on 2009-09-11
I accidentally deleted this widget from my panel, and I can not get it back. 

Please note that I am NOT talking about nm-connection-editor that shows wired/wireless/broadband/VPN/DSL tabs. I mean that widget that shows you the current wireless networks in the area and you can choose which one to connect to.

I think this may be a trivial problem, but I can get it back after deleting it!

---

### Post by Ocxic on 2009-09-11
alt-f2

and run "nm-applet" without quotes.

---

### Post by juicyoner on 2009-09-11
Thanks for the help, but this brings up what I preiously described. This is not what I am looking for. I can not select which wifi network  to connect to

I believe there is another tool different from this one

---

### Post by juicyoner on 2009-09-12
I was able to fix this w som help from here:

[http://linuxfud.wordpress.com/2007/02/14/how-to-reset-ubuntugnome-settings-to-defaults-without-re-installing/](http://linuxfud.wordpress.com/2007/02/14/how-to-reset-ubuntugnome-settings-to-defaults-without-re-installing/)

```
drop to a terminal by hitting CTRL + ALT + F1, login to your account, and run this command:

    rm -rf .gnome .gnome2 .gconf .gconfd .metacity

Get back to your GUI desktop by hitting CTRL + ALT + F7.

Login and VOILÀ! Just like the first time you ever logged into your Gnome desktop.
```

---


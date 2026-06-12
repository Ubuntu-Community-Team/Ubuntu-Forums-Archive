---
title: "Ubuntu Lucid Login Screen Customization"
date: 2010-05-21
forum: General Help
---

### Post by LKNT on 2010-05-21
Hi everyone,

I am trying to customize the login screen on Ubuntu 10.04. I know about that way of running:

```
sudo cp /usr/share/applications/gnome-appearance-properties.desktop /usr/share/gdm/autostart/LoginWindow/

```

then logging out, changing the wallpaper, logging back in and running:

```
sudo unlink /usr/share/gdm/autostart/LoginWindow/gnome-appearance-properties.desktop
```

But that only lets me change the wallpaper, so now I have my own wallpaper but the login window (where you choose the username and enter the password) is in the middle of the screen covering my image. I would need to move it a bit to the side/corner, would this be possible? I took a look at the file /usr/share/gdm/gdm-greeter-login-window.ui, however it doesn't seem to be allowing you to change the position of the window.

All help is appreciated!

P.S. This is actually not for me, so please don't start trying to convince me to give this up, as it doesn't depend on me. :-)

---

### Post by LKNT on 2010-05-24
Anybody? It's quite important :(

---

### Post by philinux on 2010-05-24
[http://www.ubuntugeek.com/gdm2-setup-a-login-interface-management-utility-for-the-new-gdm.html](http://www.ubuntugeek.com/gdm2-setup-a-login-interface-management-utility-for-the-new-gdm.html)

Or there's a deb file. [https://launchpad.net/gdm2setup](https://launchpad.net/gdm2setup)

---

### Post by LKNT on 2010-05-24
Thanks for the reply, however my problem is this: There is a background image, however the middle of it (which we want visible) is covered by the login prompt. Therefore we would like to move the login prompt a bit away from the center of the screen. Would that be possible?

Anyway thanks again for the reply!

---

### Post by growlf on 2010-06-01
So far, the new GDM does not allow for positioning the login window at all.  So, other add-ons like GDM2Setup cant help even in that department.  Sorry.

---

### Post by hellblazer on 2010-07-09
I'm also interested in changing the login theme, but I don't even want to do anything wild, all I want to know is how do I apply one of the 12 themes already installed in the /usr/share/gdm/themes directory?

Surely they wouldn't be included if there was no way to use them?

---

### Post by sjhaffner on 2010-07-09
I've been trying to find a way to do this also, this is what I found:

[http://www.ubuntugeek.com/gdm2-setup-a-login-interface-management-utility-for-the-new-gdm.html](http://www.ubuntugeek.com/gdm2-setup-a-login-interface-management-utility-for-the-new-gdm.html)

It works for me!

---


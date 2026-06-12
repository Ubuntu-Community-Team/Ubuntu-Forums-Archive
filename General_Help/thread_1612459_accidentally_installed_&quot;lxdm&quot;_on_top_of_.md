---
title: "accidentally installed &quot;lxdm&quot; on top of Ubuntu 10.10"
date: 2010-11-03
forum: General Help
---

### Post by j3k2008 on 2010-11-03
I'm using 10.10, up to date etc. I went into Synaptic Package Manager and installed the package "ldxm" and all its dependancies.

Now when I go to log into Gnome desktop, all I can see is my wallpaper. HELP!

All my girlfriend's files and photos were encrypted in the home directory (or whatever), I selected that option when I installed it.

All I wanted was the new login-screen theme (rather than the rectangular default one) and now I can't seem to revert back

Can anyone help me out here? I just want to go back to before I installed "lxdm"

Kindest Regards!

---

### Post by philinux on 2010-11-03
> **j3k2008 said:**
> I'm using 10.10, up to date etc. I went into Synaptic Package Manager and installed the package "ldxm" and all its dependancies.

Now when I go to log into Gnome desktop, all I can see is my wallpaper. HELP!

All my girlfriend's files and photos were encrypted in the home directory (or whatever), I selected that option when I installed it.

All I wanted was the new login-screen theme (rather than the rectangular default one) and now I can't seem to revert back

Can anyone help me out here? I just want to go back to before I installed "lxdm"

Kindest Regards!

At the login screen choose Session and select Gnome.

---

### Post by j3k2008 on 2010-11-03
> **philinux said:**
> At the login screen choose Session and select Gnome.

I have the following options:

Default
LXDE
KDE/Openbox
Recovery console
guest-restricted
guest-restricted
Openbox Session
guest-restricted
Ubuntu Desktop Edition
User Defined Session
Ubuntu Desktop Edition (Safe Mode)
Gnome/Openbox

and when I select "Gnome/Openbox" it comes up with a message box that says

> "Could not update ICEauthority file /home/aimee/.ICEauthority"

then it comes up with

> Nautilus could not create the following required folders: /home/username/Desktop,/home/aimee/.nautilus
Before running Nautilus, please create these folders, or set permissions such that Nautilus can create them.

:'(

---

### Post by philinux on 2010-11-03
Choose ubuntu desktop edition.

---

### Post by j3k2008 on 2010-11-03
> **philinux said:**
> Choose ubuntu desktop edition.

Same thing happens, Naulitus cannot load etc

edit:
this time I also get a message
> There is a problem with the configuration server.
(/usr/lib/libgconf2-4/gconf-sanity-check-2 exited with status 256)

---

### Post by j3k2008 on 2010-11-03
also, when encrypted the home folder, i entered a paraphrase. A bunch of text (it looked like a long string of random text) appeared underneeth it. I did not write this down, but I remember the paraphrase I entered (aimee)

I tried to do this:
[https://help.ubuntu.com/community/EncryptedPrivateDirectory#Recovering%20Your%20Data%20Manually](https://help.ubuntu.com/community/EncryptedPrivateDirectory#Recovering%20Your%20Data%20Manually)

but it won't mount :cry:

---

### Post by sisco311 on 2010-11-03
Change the default display manager to GDM:
```
sudo dpkg-reconfigure -fgnome gdm
```

---

### Post by j3k2008 on 2010-11-03
> **sisco311 said:**
> Change the default display manager to GDM:
```
sudo dpkg-reconfigure -fgnome gdm
```

Ok, I logged into Recovery console, typed that command, a window popped up and I selected gdm instead of lxdm.... restarted and VIOLA !

YOU SIR ARE MY SAVIOUR ! I AM ETERNALLY IN YOUR DEBT ! ASK ME ANYTHING!

---


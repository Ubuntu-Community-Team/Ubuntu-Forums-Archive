---
title: "Removing Unity"
date: 2010-11-20
forum: General Help
---

### Post by racie on 2010-11-20
Out of curiosity, I installed Unity on my desktop install of Ubuntu via
```
sudo apt-get install ubuntu-netbook
```

While I love the look and the idea, I found Unity to be VERY slow on my machine so I want to remove it.  I am aware that I could just pick the desktop edition when I start up, but I would like Unity completely removed.

I found these instructions, but I want to know if this is correct for my situation:
```
apt-get --auto-remove purge unity
apt-get --auto-remove purge ubuntu-netbook-default-settings
apt-get --auto-remove purge mutter
```

I'm thinking this isn't right for me as I already have the desktop session installed.

---

### Post by racie on 2010-11-21
Anyone?

---

### Post by WorMzy on 2010-11-21
Unfortunately, since that package is a metapackage, there is no way for us to know exactly which packages you should keep installed, and which ones you should remove. Check through your apt logs (/var/log/apt) and search for "unity". Hopefully the line that contains that package will also contain a list of all the packages that were installed at the same time. Once you have that information, you can remove them with a simple

```
sudo apt-get purge [package1] [package2]...
```

---

### Post by racie on 2010-11-21
> **WorMzy said:**
> Unfortunately, since that package is a metapackage, there is no way for us to know exactly which packages you should keep installed, and which ones you should remove. Check through your apt logs (/var/log/apt) and search for "unity". Hopefully the line that contains that package will also contain a list of all the packages that were installed at the same time. Once you have that information, you can remove them with a simple

```
sudo apt-get purge [package1] [package2]...
```

Ahh thanks.  There's a neat little list of everything that got installed. :D

One more question though...

All of the entries look similar to this one:
```
unity-asset-pool:i386 (0.8.18-0ubuntu1, automatic)
```

Do I only need ```
unity-asset-pool
``` or do I need the complete line like this ```
unity-asset-pool:i386 (0.8.18-0ubuntu1, automatic)
```?


Thanks again.

---

### Post by dcstar on 2010-11-21
Stop stuffing around with the command line and use Synaptic to remove the packages - that is what it is for.

---

### Post by racie on 2010-11-21
> **dcstar said:**
> Stop stuffing around with the command line and use Synaptic to remove the packages - that is what it is for.

I'd rather do it with one quick line in terminal as there are way too many packages to be removed.  I don't think the extra text is needed anyway.

*edit*  Here is a list of the packages.  I know that some of them definitely need to be removed, but some are applications, and I have no idea what some of the other ones do.  I don't want to uninstall necessary system packages.  :/

```
unity-asset-pool
unity mutter-common
libunity0
appmenu-gtk
libzeitgeist-gio
libxcb-icccm1
libmutter-private0
cheese
quadrapassel
unity-place-applications
bamfdaemon
gnome-mahjongg
libglew1.5
cheese-common
libxcb-property1
simple-scan
firefox
libclutk-0.3-0
ubuntu-netbook
libdee-1.0-0
firefox-gnome-support
unity-place-files
indicator-datetime
indicator-appmenu
libcheese-gtk18
ubuntu-netbook-default-settings
libunity-misc0
firefox-branding
gwibber
libbamf0
mutter
```

---

### Post by WorMzy on 2010-11-22
> **racie said:**
> Do I only need ```
unity-asset-pool
``` or do I need the complete line like this ```
unity-asset-pool:i386 (0.8.18-0ubuntu1, automatic)
```?

Nah, you don't need the information after the colon (: ), just the name of the package.

Obviously, you'd be safe removing anything with unity in it's name. ubuntu-netbook-default-settings and ubuntu-netbook can go too, for the same reason.
Mutter is the window manager, so you can remove that (and associated packages) if you use metacity or compiz. libclutk, bamfdaemon and libbamf0 can go too, since they were dragged in for mutter (window matching and clutter).
Cheese is a webcam app, gwibber is a social networking website client, firefox is a web browser, quadrapassel and gnome-mahjongg are both games, so if you don't use any of these, they can go.
Simple-scan is a scanner app. If you don't have/use a scanner, it can go.

Not sure about indicator-datetime or indicator-appmenu, but I assume they're similar to the gnome-panel clock and custom-menu applets. They can probably go.

The others (appmenu-gtk libzeitgeist-gio libxcb-icccm1 libglew1.5 libxcb-property1 libdee-1.0-0) are probably safe to go, but I'd remove them one by one, and make sure they won't take half your system with them.


> Stop stuffing around with the command line and use Synaptic to remove the packages - that is what it is for. 

Just because there is a GUI, doesn't mean you have to use it. :|

---

### Post by racie on 2010-11-22
Well, I went for all or nothing and removed them all.  :P  At first, I did them one by one, but it asked if I wanted to auto-remove all of the packages that were dependent on the Unity and mutter packages and I chose to do so.  Nothing seems to have broken after logging out and back in... heh.

Thanks for your help!

*edit*  I just rebooted and noticed that Unity is no longer a choice for the desktop environment at login. :D

---


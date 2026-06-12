---
title: "Updating gdk, glib, gtk+, etc libraries has broken my GTK+ window/icon theme"
date: 2011-05-05
forum: General Help
---

### Post by mercnet on 2011-05-05
I was trying to install Audacious 2.5 which required new libraries:
[LIST]
[*]gdk-pixbuf-2.22.1
[*]glib-2.28.6
[*]gtk+-2.24.4
[*]libmowgli-60e2589fc14e
[*]pango-1.28.4
[/LIST]

I performed the following commands to build them:
```

./configure
make
sudo make install

```

I rebooted and now my current window/icon theme is missing and gives the following error:
> This theme will not look as intended because the required GTK+ theme 'eco' is not installed".


If I look at synaptic, it shows it as being installed (see screenshot). How do I go about rolling back the library updates I made? I tried reinstalling the themes from synaptic but so far no luck.

---

### Post by andrewthomas on 2011-05-05
This ppa

[https://launchpad.net/~nilarimogard/+archive/webupd8]("https://launchpad.net/%7Enilarimogard/+archive/webupd8")

has audacious-2.5.0.

> **mercnet said:**
> 
I performed the following commands to build them:
```

./configure
make
sudo make install

``` How do I go about rolling back the library updates I made?

this is why you should use checkinstall instead of make install, in order to build a .deb that can be easily removed.

[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

[https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)

[https://help.ubuntu.com/community/CheckInstall](https://help.ubuntu.com/community/CheckInstall)

You may have to manually remove the files, or look inside the directory that you built in at the makefile, there may be a make uninstall target.

---

### Post by mercnet on 2011-05-06
Wow thank you so much. Command 'make uninstall' worked and fixed everything. I will now only use checkinstall, thanks for the tip.

---


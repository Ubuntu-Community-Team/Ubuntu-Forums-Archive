---
title: "Desktop enviroments"
date: 2009-06-29
forum: General Help
---

### Post by Bearded-flower on 2009-06-29
Ok with the downfall of gnome 3 i got to thinking.
what are some other desktop managers?
i know about flux box XFCE KDE (NO, KDE IS NOT A POSSIBILITY)
experiences, screenshots anything.

---

### Post by kerry_s on 2009-06-29
there are only a few desktops, the rest are "window managers".

i bank on xfce4 moving to the head of the pack. ;)

---

### Post by t4thfavor on 2009-06-29
if window managers is what you meant, the only ones I know that are complete, and glitzy are KDE, and Gnome.

XFCE, and fluxbox are lightweight, and leave me wanting.


Downall of Gnome 3? Did I miss some news?

---

### Post by LinkinCable on 2009-06-29
Joe's Window Manager JMW very light, its used in Puppylinux

---

### Post by lovinglinux on 2009-06-29
I'm on a crossroad due to the same reason. So far, I don't like Gnome Shell and I'm searching for alternatives, specially because I want to be able to run Compiz. It seems that Gnome Shell will not run Compiz without the loss of functionality. I'm not sure what functionality will be lost, but if I just won't be able to use the panel, then I won't miss Gnome Shell et all.

KDE is not an alternative for me. I like the plasma thing and KDE panel, but prefer Gnome applications and themes. So I'm already trying to get rid o my dependency on the panel. Here is my recipe:

1) remove all applets from the panel and make it transparent

2) open gconf-editor, then select "panel >> toplevels >> panel_# (probably panel_0)", then set the panel options like this:

auto-hide: yes
auto_hide_size: 0
hide-delay: 0
unhide-delay: 1000
size: 0
orientation: bottom

This way the panel will be less intrusive almost imperceptible. I use the bottom orientation because I also use awn dock, so it covers the panel and prevent it from unhide accidentally.

All menu related stuff can be accomplished with "Run Application" or Gnome-do (I don't like it) and awn, which has a nice application menu applet btw. See attached screen shot.

I'm also experimenting running gnome with plasma, so I can use KDE panel and widgets, without all the bundled kde software and configuration tools.

This is the way I'm doing:

1) Install kde-core, which comes with just the necessary packages to work. It doesn't come with all bundled KDE applications, so it doesn't clog the gnome menu with unnecessary applications.

```
sudo ap-get install kde-core
```

When it asks if you want to use gdm or the "kthing", choose gdm.

2) Install plasma, compiz-kde and compizconfig-backend-kconfig

```
sudo apt-get install plasma compiz-kde compizconfig-backend-kconfig
```

Then log into a GNOME session and launch plasma through the "Run Application" tool (ALT+F2).

The only thing I'm not happy yet, is a way to easily monitor CPU usage, network activity and hdd activity. The system monitor applet of Gnome panel is great, but I don't like the panel itself. The kde panel is very beautiful, but I don't like the system monitor and it doesn't offer an hdd activity app. The screenlets system monitor would work, but it is buggy and hard to make several instances of it to stick. Besides, I like to be able to monitor system resources through the panel, not on a widget or widget layer.

Anyways, with these settings I realized I can run some bells and whistles from kde without running a kde desktop. Maybe this way it will also be an option for you.

---

### Post by Bearded-flower on 2009-06-30
Yeah i really like fluxbox but i really dont wanna have to make a code just to set a wallpaper, that and no compiz 
///tear

---

### Post by Bearded-flower on 2009-07-01
Anyother ideas?

---

### Post by geo909 on 2009-07-01
The most popular desktop environments for linux are Gnome, KDE, xfce and lxde. Maybe the only ones, I don't know. If you don't like any of them you will need to go with a barebones window manager. And then, yes, you will have to edit configuation files and do most things by hand. Another possibility is to use gnome/kde with an alternative window manager, but that will also be a pain if you want to avoid DIY stuff..

So you don't like *any* of the above mentioned desktops?!

---

### Post by Bearded-flower on 2009-07-01
At the moment im using KDE its ARGH I CAANT SAY IT!
its not to bad.
i guess.

---

### Post by stanca on 2009-08-02
How about E17+Ecomorph(compiz like)?:popcorn:

---

### Post by Mark76 on 2009-08-02
> **geo909 said:**
> The most popular desktop environments for linux are Gnome, KDE, xfce and lxde. Maybe the only ones, I don't know. If you don't like any of them you will need to go with a barebones window manager. And then, yes, you will have to edit configuation files and do most things by hand. Another possibility is to use gnome/kde with an alternative window manager, but that will also be a pain if you want to avoid DIY stuff..

So you don't like *any* of the above mentioned desktops?!

There's also ROX Desktop. But it doesn't work like any of the above (the nearest mainstream equivalent would be Xfce. But that's only because both take a modular approach) due to its use of zeroinstall.

---

### Post by Bearded-flower on 2009-08-03
Ok?
ill... think about it?

---


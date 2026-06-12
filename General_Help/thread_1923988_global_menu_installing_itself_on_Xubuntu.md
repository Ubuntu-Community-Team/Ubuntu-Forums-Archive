---
title: "global menu installing itself on Xubuntu?"
date: 2012-02-11
forum: General Help
---

### Post by godsgifttoearth on 2012-02-11
how desktop used to look before update.

[IMG]http://i43.tinypic.com/sdogbd.jpg[/IMG]

how desktop looks now after update if nautilus is started. once nautilus is killed via task manager stupid global menu goes away.

[IMG]http://i39.tinypic.com/20zb89f.jpg[/IMG]

why has unity installed itself on my XFCE desktop? its stupid, i hate it and why i use XFCE. how do i get rid of it? how do i disbale global menu? how do i make it normal again?

thanks for your help.

---

### Post by 3Miro on 2012-02-11
Here is an awesome page, just Ctr+F search for Global Menu:

[http://www.webupd8.org/2011/10/things-to-tweak-after-installing-ubuntu.html](http://www.webupd8.org/2011/10/things-to-tweak-after-installing-ubuntu.html)

Presumably the command is:

```
sudo apt-get remove appmenu-gtk3 appmenu-gtk appmenu-qt
```

They also have a command to remove the side handles and restore the regular scroll bars.

---

### Post by godsgifttoearth on 2012-02-11
> **3Miro said:**
> Here is an awesome page, just Ctr+F search for Global Menu:

[http://www.webupd8.org/2011/10/things-to-tweak-after-installing-ubuntu.html](http://www.webupd8.org/2011/10/things-to-tweak-after-installing-ubuntu.html)

Presumably the command is:

```
sudo apt-get remove appmenu-gtk3 appmenu-gtk appmenu-qt
```

They also have a command to remove the side handles and restore the regular scroll bars.

sadly doesn't work, still stuck with it. couldn't find anything on that site (regular browser) that met this problem. something keeps installing unity 2d and i can't work out what it is.

is there some way to see which packages might be relying on unity or something similar, i tried to completely remove unity but it then says it needs to install stuff in order to complete it so clearly something is using the files and its wrongly loading. i just lack the ability to sort this out as i'm still very much a GUI level of unix competence.

---

### Post by ajgreeny on 2012-02-11
I think this is mainly a problem of you opening nautilus in xubuntu, as it then takes over drawing the desktop from whatever normally does it in xubuntu.  On my xubuntu 11.10 with nautilus installed I loose the chosen wallpaper while nautilus is running, but all returns to a normal xubuntu desktop when nautilus is closed.

The same happens in Lubuntu 11.04, but there it is possible to stop nautilus drawing the desktop by editing the appropriate key in gconf-editor, not now possible in xubuntu 11.10, and I don't know where that control is in gtk3 and gnome 3.

See if you can find out with a search of these forums or elsewhere.

---

### Post by godsgifttoearth on 2012-02-11
> **ajgreeny said:**
> I think this is mainly a problem of you opening nautilus in xubuntu, as it then takes over drawing the desktop from whatever normally does it in xubuntu.  On my xubuntu 11.10 with nautilus installed I loose the chosen wallpaper while nautilus is running, but all returns to a normal xubuntu desktop when nautilus is closed.

The same happens in Lubuntu 11.04, but there it is possible to stop nautilus drawing the desktop by editing the appropriate key in gconf-editor, not now possible in xubuntu 11.10, and I don't know where that control is in gtk3 and gnome 3.

See if you can find out with a search of these forums or elsewhere.

i've had nautilus installed from the very beginning and it has only just started doing it. something has changed since the last wave of updates i applied in the last few days but i don't know how to figure out how to change it. i'd use thunar but the stupid network lag that makes it take about 30secs to open a window annoyed me to the point of madness.

---

### Post by 3Miro on 2012-02-11
On the web-page that I posted, there is an explanation on how to prevent Nautilus from drawing the background. Maybe that will help.

Ubuntu 11.10 was the first release that doesn't come with Synaptic Package Manager installed by default. I install it anyway:
```
sudo apt-get install synaptic
```

From there, you can see a lot of detailed information on which package depends on which and why things get installed.

BTW, I have Ubuntu with XFCE installed. If I run Nautilus it does take over the background, but it doesn't come with a global menu. My system is up-to-date, so the issue is probably with the settings on yours (which means it can be fixed).

---

### Post by godsgifttoearth on 2012-02-11
> **3Miro said:**
> On the web-page that I posted, there is an explanation on how to prevent Nautilus from drawing the background. Maybe that will help.

Ubuntu 11.10 was the first release that doesn't come with Synaptic Package Manager installed by default. I install it anyway:
```
sudo apt-get install synaptic
```

From there, you can see a lot of detailed information on which package depends on which and why things get installed.

BTW, I have Ubuntu with XFCE installed. If I run Nautilus it does take over the background, but it doesn't come with a global menu. My system is up-to-date, so the issue is probably with the settings on yours (which means it can be fixed).

ok stopping nautilus drawing the desktop removes global menu, but now i have no icons for the files, meh, never usually have items there.

thanks for the help, sorry for missing the info in your first attempt.

---

### Post by 3Miro on 2012-02-11
> **godsgifttoearth said:**
> ok stopping nautilus drawing the desktop removes global menu, but now i have no icons for the files, meh, never usually have items there.

thanks for the help, sorry for missing the info in your first attempt.

Did the Icon theme got messed. Maybe you uninstalled it by mistake. Go to XFCE Settings Manager and Appearance, then you can select an icon theme. You can also install icon themes from Synaptic.

---


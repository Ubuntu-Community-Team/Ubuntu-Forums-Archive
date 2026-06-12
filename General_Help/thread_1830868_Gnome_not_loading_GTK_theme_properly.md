---
title: "Gnome not loading GTK theme properly"
date: 2011-08-22
forum: General Help
---

### Post by Kallun on 2011-08-22
Hello there :D

I hope someone can help with this, it's pretty damn frustrating!

I just completed my new build, got elementary running on it (for anyone who doesn't know, it's built on top of Ubuntu 10.10).

Everything's running nice and smooth, except for just one thing that's REALLY bugging me... every time I log in, gnome seems to launch with the sort of 'Hi colour' GTK theme, so to speak:

[IMG]http://i56.tinypic.com/ohuzpl.png[/IMG]

To get it to load my GTK theme (elementary) I have to log out and back in multiple times, in which the number of times this is done is inconsistent, perhaps it relies on how long I leave it at the logon screen.

Quite frustrating, as I'm sure you can imagine. I'm using the NVidia proprietary drivers, which haven't caused any issues as far as I'm aware.

Thanks for reading, any help on this is greatly appreciated, thanks in advance :)

---

### Post by artemgab on 2011-08-24
Hi. I have this bug too. Sometimes I log on just to discover that the default GTK theme is being used. Like you, I think this is somehow related with the time at logon screen: the more the time - the more likely the theme will be screwed.
Some people on the net suggest the problem is with the gnome-settings-daemon. See for example bug [https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/574296](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/574296). I'm going o try to reinstall everything synaptic finds with "gnome-settings-daemon" pattern.

---

### Post by artemgab on 2011-08-29
unfortunately, reinstalling packages which are found via gnome-settings-daemon query, didn't help. but I found one more similar bug that has been annoying people since 1010. [649809]("https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/649809")

---


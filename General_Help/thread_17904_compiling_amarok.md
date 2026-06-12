---
title: "compiling amarok"
date: 2005-03-03
forum: General Help
---

### Post by spacemonkey on 2005-03-03
I'm running Warty and I am trying to compile amarok, the music player/library.  I know you can get it via the debian repositories, but I don't know much about that and have heard a lot of people saying that it can mess things up.

I used apt-get to install build essentials and ran ./configure, it goes through quite a bit of stuff and then gives an error.  The error says:

Checking for X... configure: error: Can't find X includes.  Please check your installation and add the correct paths!

I'm not really sure what it's asking me to do.  Any suggestions would be greatly appreciated.  Thanks.

---

### Post by p!=f on 2005-03-03
[QUOTE=spacemonkey]I'm running Warty and I am trying to compile amarok, the music player/library.  I know you can get it via the debian repositories, but I don't know much about that and have heard a lot of people saying that it can mess things up.

I used apt-get to install build essentials and ran ./configure, it goes through quite a bit of stuff and then gives an error.  The error says:

Checking for X... configure: error: Can't find X includes.  Please check your installation and add the correct paths!

I'm not really sure what it's asking me to do.  Any suggestions would be greatly appreciated.  Thanks.[/QUOTE]
```

sudo apt-get install x-dev x-window-system-dev

```
should be sufficient. You could, however, need additional development (-dev) packages to satisfy amarok's dependencies during ./configure.

---

### Post by spacemonkey on 2005-03-03
that helped, it got farther this time, but now it said this:

checking for Qt... configure: error: Qt (>= Qt 3.2) (headers and libraries) not found. Please check your installation!

Again, not really sure what that means.  As far as dependencies, it says it requires these:

    * KDE-Libs 3.2
      [http://www.kde.org](http://www.kde.org)

    * TagLib 1.3.1
      (metadata tagging library)
      [http://freshmeat.net/projects/taglib](http://freshmeat.net/projects/taglib)

I've installed these, or atleast what I thought were these packages, via synaptic.  I'm not sure what Qt is, but it said Qt 3.2, could that have something to do with the KDE-Libs since it needs 3.2 there also?  Thanks for the help.

[edit]
Another thing...I just got the KDE-Libs package, not the -dev one.  Could that be the problem?  It doesn't say -dev in the amarok README file however.

---

### Post by p!=f on 2005-03-03
[QUOTE=spacemonkey]that helped, it got farther this time, but now it said this:

checking for Qt... configure: error: Qt (>= Qt 3.2) (headers and libraries) not found. Please check your installation!

Again, not really sure what that means.  As far as dependencies, it says it requires these:

    * KDE-Libs 3.2
      [http://www.kde.org](http://www.kde.org)

    * TagLib 1.3.1
      (metadata tagging library)
      [http://freshmeat.net/projects/taglib](http://freshmeat.net/projects/taglib)

I've installed these, or atleast what I thought were these packages, via synaptic.  I'm not sure what Qt is, but it said Qt 3.2, could that have something to do with the KDE-Libs since it needs 3.2 there also?  Thanks for the help.

[edit]
Another thing...I just got the KDE-Libs package, not the -dev one.  Could that be the problem?  It doesn't say -dev in the amarok README file however.[/QUOTE]
I don't use KDE but installing 
```

sudo apt-get install {kdelibs4,libqt3,libtagc0,libtag1}-dev

```
could move you forward. :)

---

### Post by spacemonkey on 2005-03-03
So I did some fiddling around and managed to get it to move a little further.  It goes all the way to the end of configure, but it says it can't find gstreamer, but I know it's installed.  It says something about changing the pkg_config_path or something like that.  The readme says I should do export PKG_CONFIG_PATH="/path/to/gstreamer-0.x.y.pc" and then reconfigure.  But I searched for gstreamer-0.8.pc and it couldn't find that file.  Any suggestions?

---

### Post by p!=f on 2005-03-03
[QUOTE=spacemonkey]So I did some fiddling around and managed to get it to move a little further.  It goes all the way to the end of configure, but it says it can't find gstreamer, but I know it's installed.  It says something about changing the pkg_config_path or something like that.  The readme says I should do export PKG_CONFIG_PATH="/path/to/gstreamer-0.x.y.pc" and then reconfigure.  But I searched for gstreamer-0.8.pc and it couldn't find that file.  Any suggestions?[/QUOTE]
Again, missing -dev package. :)
```

[~] > dpkg -S `locate gstreamer-0.8.pc`
libgstreamer0.8-dev: /usr/lib/pkgconfig/gstreamer-0.8.pc

```

---

### Post by spacemonkey on 2005-03-03
IT WORKS!!! Finally.  Thanks so much for the help.  I think I needed this struggle to help me learn about compiling.  Important lesson of the day..... you need the -dev package if you're compiling.  One question though....it looks kinda messy, as I expected since its a KDE app, and suggestions on making it look better, other than running KDE?

---


---
title: "Random Nautilus Crashes"
date: 2012-01-26
forum: General Help
---

### Post by Joseph Schwenker on 2012-01-26
I'm on Ubuntu 11.04 32-bit with Nautilus 2.32.2.1, and I've been experiencing random Nautilus crashes for several months. They happen as follows:

1) Nautilus is started
2) Nautilus runs as expectedly
3) Nautilus either suddenly crashes (often when performing an action like creating a folder or opening a properties window) or produces strange behavior, like missing context menu items

Here's the terminal output from one of the times when Nautilus crashed:

```
joseph@joseph:~$ killall -9 nautilus && nautilus
Initializing nautilus-gdu extension

(nautilus:21642): IBUS-WARNING **: Connect to unix:abstract=/tmp/dbus-7f3wLJATiY,guid=c5f3450f222ef115949bf0e800000040 failed: Failed to connect to socket /tmp/dbus-7f3wLJATiY: Connection refused.

(nautilus:21642): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:21642): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:21642): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:21642): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:21642): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:21642): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:21642): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


(nautilus:21642): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:21642): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:21642): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:21642): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:21642): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:21642): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:21642): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:21642): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:21642): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:21642): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:21642): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:21642): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:21642): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:21642): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:21642): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:21642): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:21642): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:21642): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:21642): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:21642): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:21642): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:21642): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:21642): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:21642): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:21642): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:21642): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:21642): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:21642): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:21642): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:21642): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:21642): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:21642): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:21642): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:21642): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:21642): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:21642): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:21642): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:21642): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:21642): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:21642): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed

(nautilus:21642): GLib-GObject-CRITICAL **: g_value_get_object: assertion `G_VALUE_HOLDS_OBJECT (value)' failed
**
ERROR:fm-directory-view.c:1411:action_new_folder_callback: assertion failed: (FM_IS_DIRECTORY_VIEW (callback_data))
Aborted

```

I've attached a screenshot demonstrating frequent missing context menu items ("Open", "Open in New Tab", "Open in New Window", and "Open With Other Application..." are missing when right-clicking on a folder) which often precede Nautilus crashes.

Is this a known issue, and is there a fix, or an updated version, available?

---

### Post by Joseph Schwenker on 2012-01-28
bump

---

### Post by PGScooter on 2012-01-29
have you tried reinstalling?

You could always give dolphin a shot. I think that it is great. It is the file manager for Kubuntu. The only thing is you will have to install some KDE libraries but that is just a question of space. Nothing else should be affected.

---

### Post by Joseph Schwenker on 2012-01-29
> **PGScooter said:**
> have you tried reinstalling?

You could always give dolphin a shot. I think that it is great. It is the file manager for Kubuntu. The only thing is you will have to install some KDE libraries but that is just a question of space. Nothing else should be affected.

I've tried reinstalling several times, but to no avail. I've been using Nautilus for as long as I've been on Linux, though I have tried several other file managers, none of which satisfied my needs.

---

### Post by PGScooter on 2012-01-29
Yeah I know what you mean. Once you find an app you're comfortable with you don't want to get used to another. Well, I would file a bug report if I were you. Either here:
[https://bugs.launchpad.net/ubuntu/+source/nautilus/](https://bugs.launchpad.net/ubuntu/+source/nautilus/)
or here:
[https://bugzilla.gnome.org/enter_bug.cgi?product=nautilus](https://bugzilla.gnome.org/enter_bug.cgi?product=nautilus)

And then, if you're up for it, I would recommend compiling from source. Download from here:
[http://live.gnome.org/Nautilus/Downloads](http://live.gnome.org/Nautilus/Downloads)
My guess is you'll have the same problem with the stable release 2.32. So why not give development a shot? Go here
[http://ftp.acc.umu.se/pub/GNOME/sources/nautilus/3.3/](http://ftp.acc.umu.se/pub/GNOME/sources/nautilus/3.3/)
download the source code. When I built it it was very straightforward. ie I think it was just ./configure; make; sudo make install
of course you have to make sure you have all of the dependencies to do that. To install most, if not all of the dependencies, do a sudo apt-get build-dep nautilus

---

### Post by Joseph Schwenker on 2012-01-30
> **PGScooter said:**
> Yeah I know what you mean. Once you find an app you're comfortable with you don't want to get used to another. Well, I would file a bug report if I were you. Either here:
[https://bugs.launchpad.net/ubuntu/+source/nautilus/](https://bugs.launchpad.net/ubuntu/+source/nautilus/)
or here:
[https://bugzilla.gnome.org/enter_bug.cgi?product=nautilus](https://bugzilla.gnome.org/enter_bug.cgi?product=nautilus)

And then, if you're up for it, I would recommend compiling from source. Download from here:
[http://live.gnome.org/Nautilus/Downloads](http://live.gnome.org/Nautilus/Downloads)
My guess is you'll have the same problem with the stable release 2.32. So why not give development a shot? Go here
[http://ftp.acc.umu.se/pub/GNOME/sources/nautilus/3.3/](http://ftp.acc.umu.se/pub/GNOME/sources/nautilus/3.3/)
download the source code. When I built it it was very straightforward. ie I think it was just ./configure; make; sudo make install
of course you have to make sure you have all of the dependencies to do that. To install most, if not all of the dependencies, do a sudo apt-get build-dep nautilus

There appear to be fifty-seven instances of the word "crash" on the Nautilus bug page, and that's just seventy-five entries out of nine hundred six. I have no way of knowing if my issue is known or not, unfortunately. Couple that with how difficult it is to get an output when Nautilus crashes, and reporting a bug is more painful than a flying cactus to the face.

Compiling from source might be interesting--though a PPA would be much nicer. Are there any Nautilus PPA's?

---

### Post by PGScooter on 2012-01-31
> **Joseph Schwenker said:**
> There appear to be fifty-seven instances of the word "crash" on the Nautilus bug page, and that's just seventy-five entries out of nine hundred six. I have no way of knowing if my issue is known or not, unfortunately. Couple that with how difficult it is to get an output when Nautilus crashes, and reporting a bug is more painful than a flying cactus to the face.

Compiling from source might be interesting--though a PPA would be much nicer. Are there any Nautilus PPA's?

Joseph, all very good points! alas, if only bug reporting were more easy.

I do not know of a PPA, although there could be one that I don't know of. If you go the compiling by source route, post back here and I can try to help if you get stuck. But it's probably better to go to the experts:
[http://ubuntuforums.org/forumdisplay.php?f=44](http://ubuntuforums.org/forumdisplay.php?f=44)

Also, I know I already suggested it, but if you don't find a solution I would recommend using Dolphin.

---

### Post by Joseph Schwenker on 2012-01-31
> **PGScooter said:**
> Joseph, all very good points! alas, if only bug reporting were more easy.

I do not know of a PPA, although there could be one that I don't know of. If you go the compiling by source route, post back here and I can try to help if you get stuck. But it's probably better to go to the experts:
[http://ubuntuforums.org/forumdisplay.php?f=44](http://ubuntuforums.org/forumdisplay.php?f=44)

Also, I know I already suggested it, but if you don't find a solution I would recommend using Dolphin.

I tried compiling Nautilus, but it looks like [I need Gnome 3 to do so]("http://ubuntuforums.org/showthread.php?t=1678656").

I'll give Dolphin a try.

---

### Post by PGScooter on 2012-02-01
> **Joseph Schwenker said:**
> I tried compiling Nautilus, but it looks like [I need Gnome 3 to do so]("http://ubuntuforums.org/showthread.php?t=1678656").

I'll give Dolphin a try.

ah, that's unfortunate.

well I'd be interested in knowing your impressions of Dolphin after a while so post back if you get a chance.

---

### Post by Joseph Schwenker on 2012-02-01
> **PGScooter said:**
> ah, that's unfortunate.

well I'd be interested in knowing your impressions of Dolphin after a while so post back if you get a chance.

I tried Dolphin, but it wasn't to my tastes at all--it didn't fit in well with Gnome, it didn't have flippy triangles to expand directories in list view, and using it felt very awkward.

---

### Post by PGScooter on 2012-02-02
> **Joseph Schwenker said:**
> I tried Dolphin, but it wasn't to my tastes at all--it didn't fit in well with Gnome, it didn't have flippy triangles to expand directories in list view, and using it felt very awkward.

Thanks for posting your thoughts on Dolphin. Yeah it does seem a little "awkward" in Gnome. Well, I'm out of ideas then. Post back if you come up with a solution. Good luck!

---


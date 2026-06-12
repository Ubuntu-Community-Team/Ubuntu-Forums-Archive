---
title: "why nowplaying screenlet won't start?"
date: 2009-10-21
forum: General Help
---

### Post by r5r4y on 2009-10-21
Hello,
I've downloaded screenlet and I'm trying to use the screenlet called nowplaying, I've puted some themes inside /home/your_name/.screenlets/NowPlaying/themes and /usr/share/screenlet/NowPlaying/themes

but when I'm choosing to start the screenlet start/stop nothing happens... 
all others screenlets launch just fine...

Doesn't matter which player, Songbird, Rythembox, Banshee, Exaile, the screenlet won't start!

---

### Post by r5r4y on 2009-10-21
Tried runing from terminal, this is what i get:

```

False
Starter already exists.
DAEMON FOUND!

** (screenlets-manager.py:14520): WARNING **: Invalid borders specified for theme pixmap:
        /home/moshe/.themes/Lithium/gtk-2.0/Images/Scrollbars/trough-scrollbar-vert.png,
borders don't fit within the image
False
Launch NowPlaying
Launching Screenlet from: /usr/share/screenlets/NowPlaying/NowPlayingScreenlet.py
Logging output goes to: $HOME/.config/Screenlets/NowPlayingScreenlet.log
Traceback (most recent call last):
  File "/usr/share/screenlets/NowPlaying/NowPlayingScreenlet.py", line 52, in <module>
    import Theme 
  File "/var/lib/python-support/python2.6/Theme.py", line 28, in <module>
    from AvatarHistory import getLastCachedAvatar
  File "/var/lib/python-support/python2.6/AvatarHistory.py", line 27, in <module>
    from dialog import yes_no
  File "/var/lib/python-support/python2.6/dialog.py", line 25, in <module>
    import Avatar
  File "/var/lib/python-support/python2.6/Avatar.py", line 23, in <module>
    import ImageAreaSelector
  File "/var/lib/python-support/python2.6/ImageAreaSelector.py", line 38, in <module>
    class ImageAreaSelectorDialog(gtk.Dialog):
  File "/var/lib/python-support/python2.6/ImageAreaSelector.py", line 39, in ImageAreaSelectorDialog
    def __init__(self, controller, pixbuf, title = _("Select area of image"), parent = None):
NameError: name '_' is not defined


```

---

### Post by r5r4y on 2009-11-06
Seems like a problem with 9.04, It's working fine with 9.10...
But there is no songbird support. the nowplaying screenlet can't get the title and artist from Songbird.

---


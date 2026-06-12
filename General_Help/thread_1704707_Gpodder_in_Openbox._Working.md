---
title: "Gpodder in Openbox. Working?"
date: 2011-03-11
forum: General Help
---

### Post by migel_wimtore on 2011-03-11
Hi. I love gpodder, almost as much as i love openbox. However, i cannot get gpodder to run properly in openbox.

Initially it will not launch at all. This is the terminal readout:

(process:2448): Gtk-WARNING **: Locale not supported by C library.
    Using the fallback 'C' locale.
Traceback (most recent call last):
  File "/usr/bin/gpodder", line 201, in <module>
    from gpodder import gui
  File "/usr/lib/pymodules/python2.6/gpodder/gui.py", line 71, in <module>
    from gpodder import util
  File "/usr/lib/pymodules/python2.6/gpodder/util.py", line 69, in <module>
    locale.setlocale(locale.LC_ALL, '')
  File "/usr/lib/python2.6/locale.py", line 513, in setlocale
    return _setlocale(category, locale)
locale.Error: unsupported locale setting

Anyone else get that?

Anyways i can get it to run, sort of, if i first run these commands:

export LANGUAGE=en_GB.UTF-8
export LANG=en_GB.UTF-8
export LC_ALL=en_GB.UTF-8
locale-gen en_GB.UTF-8
sudo dpkg-reconfigure locales

However, one: these changes are not saved after a reboot and two: the behaviour of gpodder, when opened thusly, is strange, eg, right click becomes left click in the right column, but not the left. And also, i cannot select multiple entries at once, either with shift + arrow keys or with the mouse.

So, anyone else have similar issues? 

Im sure many people must have gpodder running fine, as it is the premium netcast application.

Also, can anyone tell me how to get the language setting to stick?

Thanks for reading.

---

### Post by migel_wimtore on 2011-03-14
Well, i found a fix for the locale thing. Which was straightforward, just had set my locale in bashrc, with the following:

export LC_ALL="en_GB.UTF-8"
export LANGUAGE="en_GB.UTF-8"
export LANG="en_GB.UTF-8"

Now thats taken care of gpodder boots up first time. However, only from the terminal. At which point it gives this readout:

** Message: pygobject_register_sinkfunc is deprecated (GstObject)

I cannot launch it from gnome menu, gnome-do nor kupfer. The run dialogue starts it like with terminal.

The behaviour within gpodder is still peculiar, of course.

Any ideas what could be causing this? Something simple perhaps? Do i have to downgrade python to handle "pygobject_register_sinkfunc"? Or install a new module to handle it? I wouldnt know where to start.

---

### Post by migel_wimtore on 2011-03-18
Gpodder works absolutely perfectly in Debian, running Openbox.

So, whatever the difference, it makes it all.

---


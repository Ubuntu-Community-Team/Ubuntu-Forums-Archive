---
title: "Remaping keys"
date: 2012-06-15
forum: General Help
---

### Post by Jaydrury1992 on 2012-06-15
Hi,

I have an issue with my keyboard which is driving me crazy, the "\" key is no longer detected as being between SHIFT and "Z" instead this is in its place " `". The backslash is now located to the left of the "1" key, all of the other keys are in the right location so what I'm asking is if there is a config file or even better a GUI to remap these specific keys without changing the layout of the whole keyboard. I know this is a long shot but its worth a try as i use the backslash frequently. 

Thanks

*Edit* I'm running Ubuntu 12.04

---

### Post by btindie on 2012-06-15
It sounds like your system may be configured to use the wrong keymap. What's the output of ```
cat /etc/default/keyboard
```For a UK keyboard you'd want something like
> XKBMODEL="pc105"
XKBLAYOUT="gb"
XKBVARIANT=""
XKBOPTIONS=""You can edit the file directly and read /usr/share/doc/keyboard-configuration/README.Debian about applying the changes or run **gnome-keyboard-properties** and click on the Layouts tab to change it to 'United Kingdom'. This is also accessible via **gnome-control-center** (System Settings).

---

### Post by Jaydrury1992 on 2012-06-15
Thanks for replying, My keyboard is set to UK already and every other key seems fine except for the two I have mentioned. Here are the results of: *cat /etc/default/keyboard*

>  # Check /usr/share/doc/keyboard-configuration/README.Debian for
# documentation on what to do after having modified this file.

# The following variables describe your keyboard and can have the same
# values as the XkbModel, XkbLayout, XkbVariant and XkbOptions options
# in /etc/X11/xorg.conf.

XKBMODEL="pc105"
XKBLAYOUT="gb"
XKBVARIANT=""
XKBOPTIONS=""

# If you don't want to use the XKB layout on the console, you can
# specify an alternative keymap.  Make sure it will be accessible
# before /usr is mounted.
# KMAP=/etc/console-setup/defkeymap.kmap.gz
I am using an Apple USB keyboard if that helps too.

---

### Post by btindie on 2012-06-15
> **Jaydrury1992 said:**
> I am using an Apple USB keyboard if that helps too.
Well that's your problem then. I haven't got any personal experience of using one myself but a quick google for *ubuntu apple keyboard* turned up various results. One in particular being [http://alandoyle.com/tutorials/slim-aluminum-apple-keyboard-under-ubuntu/](http://alandoyle.com/tutorials/slim-aluminum-apple-keyboard-under-ubuntu/) which may be of use to you.

---


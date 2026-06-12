---
title: "Keyboard Layout won't change"
date: 2012-06-21
forum: General Help
---

### Post by SterlingM on 2012-06-21
I am trying to change my default keyboard layout to colemak. If I do, setxkbmap us -variant colemak, it works until i log out. But I want the layout to be there all the time. My /etc/default/Keyboard looks like - 

```

# Check /usr/share/doc/keyboard-configuration/README.Debian for
# documentation on what to do after having modified this file.

# The following variables describe your keyboard and can have the same
# values as the XkbModel, XkbLayout, XkbVariant and XkbOptions options
# in /etc/X11/xorg.conf.

XKBMODEL="pc105"
XKBLAYOUT="us"
XKBVARIANT="colemak"
XKBOPTIONS=""

# If you don't want to use the XKB layout on the console, you can
# specify an alternative keymap.  Make sure it will be accessible
# before /usr is mounted.
# KMAP=/etc/console-setup/defkeymap.kmap.gz


```I have restarted the computer and when I log back in, it goes back to qwerty even though this file has been changed. Does anyone know why that might be? Thank you for any help.

---

### Post by SterlingM on 2012-06-21
Also, this is 12.04

---

### Post by SterlingM on 2012-06-21
bump, any ideas?

---


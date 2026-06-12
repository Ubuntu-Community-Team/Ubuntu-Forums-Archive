---
title: "disable auto open of usb drives"
date: 2012-05-02
forum: General Help
---

### Post by parminides on 2012-05-02
I did a fresh install of Ubuntu 12.04 on my HP TouchSmart, and I'm having trouble with some tweaks. I can't figure out how to disable auto open (via Nautilus) of usb drives.

In the old days of Gnome, it was easy:

```

gconftool-2 --type boolean -s /apps/nautilus/preferences/media_automount_open false

```

Or gconf-editor -> apps -> nautilus -> preferences -> uncheck media_automount_open -> change to false.

I can't find the equivalent for dconf-editor. 

Also, in Dash Home ->  System Settings -> Details -> Removable Media -> Other Media... -> Type:, there is no usb device in the list.

So how does one prevent auto opening of usb drives in Ubuntu 12.04? Note: I want the usb drives to auto mount, but not auto open.

---

### Post by parminides on 2012-05-04
I found the solution: dconf-editor -> org -> gnome -> desktop -> media-handling -> uncheck automount_open.

---

### Post by israelins85 on 2012-07-03
Hey man, thanks that works to me!

---

### Post by manyrobots on 2012-08-03
Thanks for finding that!  had the issue here.

Here is a one liner version of your find:

gsettings set org.gnome.desktop.media-handling automount-open false

---


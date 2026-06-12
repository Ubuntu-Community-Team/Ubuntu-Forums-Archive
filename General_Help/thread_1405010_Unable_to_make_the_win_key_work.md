---
title: "Unable to make the win key work"
date: 2010-02-12
forum: General Help
---

### Post by lv99782 on 2010-02-12
Hi,

I thought this should be easy to set my win key work after read many website how to configure the keyboard & keyboard short cut, but I don't know why I just can't make it work.

What I want is press win key to show panel menu

I suppose to be very simple, I went to keyboard short cut, then find Show the panel's main menu, click on short cut column, it show New shortcut, then I press win key, but nothing happen, it still show New shortcut..., when I close it change back to Alt+F1 again.

But, if I press win+F1, then it show Mod4+F1, is it possible just use Mod4 key alone to show the panel menu?

I've follow these website without luck
[http://www.howtogeek.com/howto/ubuntu/use-the-windows-key-for-the-start-menu-in-ubuntu-linux/](http://www.howtogeek.com/howto/ubuntu/use-the-windows-key-for-the-start-menu-in-ubuntu-linux/)

[http://www.addictivetips.com/ubuntu-linux-tips/launch-application-menu-in-ubuntu-with-windows-key/](http://www.addictivetips.com/ubuntu-linux-tips/launch-application-menu-in-ubuntu-with-windows-key/)

[http://guvnr.com/pc/ubuntu-windows-key/](http://guvnr.com/pc/ubuntu-windows-key/)

---

### Post by YesSir on 2010-02-12
Maybe this helps? [http://www.cyberciti.biz/faq/howto-create-keyboard-shortcuts-in-gnome/](http://www.cyberciti.biz/faq/howto-create-keyboard-shortcuts-in-gnome/)

---

### Post by wojox on 2010-02-12
Copy and paste this in the terminal:

```
gconftool-2 --set /apps/metacity/global_keybindings/panel_main_menu --type string "Super_L"
```

---

### Post by YesSir on 2010-02-12
Nice one, Wojox! ;)

---

### Post by wojox on 2010-02-12
> **YesSir said:**
> Nice one, Wojox! ;)

Yeah, I love putting that Windows key to work. ;)

---

### Post by lv99782 on 2010-02-12
Thanks, it work!

But..

this make other thing not work.  I've define Win+T to open terminal, Win+S to open search, Win+F to open File manager.  All these stop working now!

Is that mean I can't have both feature ?

---

### Post by wojox on 2010-02-12
I use F9 to open the terminal and F10 to open the File manager. You can't have both unfortunately.

It's either Windows key + F1 to open or just that little gconf hack.

---


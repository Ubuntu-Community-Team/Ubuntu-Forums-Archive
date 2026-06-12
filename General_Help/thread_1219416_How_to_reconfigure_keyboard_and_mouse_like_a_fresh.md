---
title: "How to reconfigure keyboard and mouse like a fresh install?"
date: 2009-07-21
forum: General Help
---

### Post by TheApe on 2009-07-21
Hi everybody!

I have successfully installed Jaunty on my VAIO notebook.
I've installed it using both usb external mouse and keyboard. And it works like a charm. I also had lucky configuring compiz to work with dual screen.

The problem is, when I want to use the notebook without the external stuff(mouse, keyboard and screen), it’s not working as it should be.

There are two problems:

1 - As my usb keyboard layout is different from my notebook's keyboard layout, I added a new layout at the keyboards option. It works fine, except for two points.
[INDENT]a) The keyboard layout keeps changing automatically, I can't manage to understand the behavor.
b) I couldn't get the "&ccedil" key to work. When I hit "´" and "c" the result is &#263;
[/INDENT]

2 - I get a strange behavor using the notebook's default mouse. Sometimes, I'm navigating in firefox with some tabs opened and then when I switch to other program and go back again, or switch between tabs and scroll the content, the mouse gets kind of "stuck". Or stuck on the content, or stuck on the header of FF(menus, bookmarks, etc). This behavor doesn’t happens with the external mouse. So I think it must be something with the xconf.

Well, thank's for help.

:o

---

### Post by devildoc5 on 2009-07-21
if you open up your xorg.conf does it show two different devices under input?  Such as"mouse1 and mouse0" or "Mouse1 and Touchpad"?

---

### Post by TheApe on 2009-07-21
Hi devildoc.
The only entry for mouse is the following
```

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

```

I think the touchpad isn’t properly configured. How do I configure it?

Thanks!!!!

---


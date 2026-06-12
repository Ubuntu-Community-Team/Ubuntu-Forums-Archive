---
title: "xmodmap on start"
date: 2010-08-21
forum: General Help
---

### Post by masque7 on 2010-08-21
I have a keyboard that has a backlight that toggles with **scroll lock**. The light works, and I would like to be able to have it working when I log in to X. I am using the default Gnome DE.

I run 'xmodmap  -pm' and scroll lock is shown as blank, so it's safe to use it.

```

xmodmap -e 'add mod3 = Scroll_Lock'
```
This is the command I need to use before or as X starts. This makes the function work, but only if I run that command.

For this to work globally, I made a file in */etc/X11/Xmodmap*
Containing again
```
add mod3 = Scroll_Lock
```

Unfortunately this isn't working. Any help?

---

### Post by Brandon Williams on 2010-08-22
The /etc/X11/Xmodmap file won't be applied if xkb is in use. Do you have either /etc/X11/Xkbmap or ~/.Xkbmap?

If that doesn't appear to be the problem, you could always add a 'Startup Application' to run xmodmap for you. This should work if there's something in the standard startup scripts that is over-riding the early xmodmap call in /etc/gdm/Xsession.

---

### Post by masque7 on 2010-08-22
> Do you have either /etc/X11/Xkbmap or ~/.Xkbmap?I don't have either. 

> you could always add a 'Startup Application' to run xmodmap for youTried this but wasn't sure what to use. Does this mean it would only work when logging into Gnome? If I wanted to use another DE or WM I'm guessing "Startup Applications" would be ignored? 

[Here]("http://pastebin.com/vT0PLjnk")'s my Xsession. 

Thanks :)

---

### Post by Brandon Williams on 2010-08-23
> **masque7 said:**
> Tried this but wasn't sure what to use. Does this mean it would only work when logging into Gnome? If I wanted to use another DE or WM I'm guessing "Startup Applications" would be ignored?

All the most common desktop environments support the freedesktop standards these days, including gnome, kde, and xfce. Some others do too. A startup application defined in gnome would also work in any other DE that supports the freedesktop standards.

When defining the startup application, just be sure to specify the xmodmap command line that works for you in the terminal. It should work, though I'm not sure whether all special shell symbols will function correctly, so if you're using file redirection, you might need to come up with something a little different.

---

### Post by masque7 on 2010-08-31
Just to confirm I've added a script to my startup applications

```
#!/bin/bash
xmodmap -e 'add mod3 = Scroll_Lock'
```

Works brilliantly.

---


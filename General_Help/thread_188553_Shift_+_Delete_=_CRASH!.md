---
title: "Shift + Delete = CRASH!"
date: 2006-06-04
forum: General Help
---

### Post by badrad on 2006-06-04
For the record I have compiz installed, with the instructions from this thread:
[http://www.ubuntuforums.org/showthread.php?t=131267](http://www.ubuntuforums.org/showthread.php?t=131267)
But this problem occurs even without it.

If I hold shift and press delete, no matter where I am, gnome crashes. Or I think thats what happens, Im a total Ubuntu newb. I get kicked out to a DOS looking screen with some terminal stuff on it, and in 1-10 seconds Ubuntu starts back up to the user logon screen like I just started it.

This is terribly, terribly frustrating. ANY help appreciated!

---

### Post by firetux on 2006-06-04
Are you sure it isnt shift- backspace?
If it is shift backspace do a sarch on these forums and you will find lots of similar threads.
If it really is shift-delete, check out gconf to see if there is some shortcut that kills x.

---

### Post by badrad on 2006-06-04
Sure enough - blame my late night brain for using the wrong word. Thanks for setting me on the correct track firetux.

(edit - nevermind)

I did get a fix, although its not what most people say. Adding the xmodmap to your compiz script can mess up your keyboard maps. What I found that works is here:

[http://www.compiz.net/viewtopic.php?id=610](http://www.compiz.net/viewtopic.php?id=610)

```
xmodmap -e "keycode  22 = BackSpace"
```

---

### Post by shrift on 2006-06-04
I also discovered issues with xmodmap. However if you run this after it ```
set xkb us
``` then it works correctly. So if you have a compiz/xgl script, add both commands to it, kind of like this:
```

xgl junk blblbalballbalblablabla
xmodmap /usr/share/xmodmap/xmodmap.us
set xkb us

```

That is of course for us keymaps, use a diff one if your not in the us.

---


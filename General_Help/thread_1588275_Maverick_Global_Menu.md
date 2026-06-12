---
title: "Maverick Global Menu"
date: 2010-10-04
forum: General Help
---

### Post by arvigeus on 2010-10-04
Hi! I just tested 10.10 Netbook Edition. It wasn't very good IMHO, but I really liked the global menu applet (along the option to hide window controls). Is there any way to install it in the Desktop Edition?

---

### Post by kerry_s on 2010-10-04
maximus + xdotool + indicator-applet-appmenu

hold on, let me double check, be back.
had to log out & back in for the menu to work.

ps: the menu applets a little buggy, locked up my pc. :(

---

### Post by arvigeus on 2010-10-04
Menu applet works for me. Thanks!

edit: Just to add - to make maximus less annoying, just run gconf-editor, go to apps/maximus and check "no maximize"

---

### Post by martinianom on 2010-10-05
Hi, just one question... I successfully configured everything but there's one thing that i'm missing... i can't find the path for the close, minimize, maximize buttons.. need help!! thanks

---

### Post by kerry_s on 2010-10-05
> **martinianom said:**
> Hi, just one question... I successfully configured everything but there's one thing that i'm missing... i can't find the path for the close, minimize, maximize buttons.. need help!! thanks

/usr/share/themes/Ambiance/metacity-1

---

### Post by jctots on 2010-10-13
how about the current window name? can we also put it into the panel?

---

### Post by kerry_s on 2010-10-14
> **jctots said:**
> how about the current window name? can we also put it into the panel?

look in gconf-editor see if there's a setting for that. i didn't use it long enough to look what there was.

in my current i leave the window decorations & moved the dock to the top.

---

### Post by TuxLyn on 2010-10-14
What kind of menu bar (on the bottom) does this use ? It kinds of reminds me of mac menu.

---

### Post by jctots on 2010-10-14
i looked at apps/panel/applets but haven't found the setting for the current window name...

is that a window-picker-applet?

---


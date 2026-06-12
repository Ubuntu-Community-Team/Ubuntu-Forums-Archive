---
title: "Control key won't work, think it's an xorg problem"
date: 2010-07-16
forum: General Help
---

### Post by J V on 2010-07-16
Hey, fixing a freinds computer, and apparently he's spent the last year or so without keyboard shortcuts - metacity works fine but with compiz xbindkeys doesn't even recognize the control key (But it does stop a single key from being recognised when control is held)

Control works for *setting* keyboard shortcuts, but xbindkeys can't see it, niether can most programs (Firefox, nautilus etc) but it works fine for compiz shortcuts... Switching to metacity makes the shortcuts work...

I exported without defaults, reset defaults, checked the file and found it was the viewport switcher plugin: [SOLVED]

```
*@*-desktop:~$ xbindkeys -k
Press combination of keys or/and click under the window.
You can use one of the two lines after "NoCommand"
in $HOME/.xbindkeysrc to bind a key.
"NoCommand"
    m:0x10 + c:54
    Mod2 + c
*@*-desktop:~$ xbindkeys -k
Press combination of keys or/and click under the window.
You can use one of the two lines after "NoCommand"
in $HOME/.xbindkeysrc to bind a key.
"NoCommand"
    m:0x10 + c:54
    Mod2 + c
*@*-desktop:~$ xbindkeys -k
Press combination of keys or/and click under the window.
You can use one of the two lines after "NoCommand"
in $HOME/.xbindkeysrc to bind a key.
"NoCommand"
    m:0x10 + c:38
    Mod2 + a
```

---


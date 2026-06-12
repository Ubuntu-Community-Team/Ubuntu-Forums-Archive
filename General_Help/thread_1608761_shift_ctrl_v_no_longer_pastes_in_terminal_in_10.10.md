---
title: "shift ctrl v no longer pastes in terminal in 10.10"
date: 2010-10-29
forum: General Help
---

### Post by Budoc on 2010-10-29
Hi all,

I have noticed since installing ubuntu 10.10 a few weeks back, that pasting into terminals no longer works as expected. In earlier releases, shift+ctrl+v would paste the contents of the clipboard to the terminal. However, now shift+ctrl+v no longer does this. According to the keyboard shortcuts window, shift+ctrl+v is the shortcut for pasting. I can temporarily get shift+ctrl+v to paste if I enter the following code into a terminal:

```
gconftool-2 --type string --set /apps/gnome-terminal/keybindings/paste '<Ctrl><Shift>v'
```

but if I close the terminal and re-open it, the shift+ctrl+v shortcut will only enable me to paste for a while before the shortcut does nothing. Shift+Ins works normally.

How can I find out if another program is using this keybinding and thus preventing me from pasting in a terminal? I've looked in System > Preferences > Keyboard Shortcuts but there's nothing relevant in there. Is there a program that I can run to see how the system responds to me pressing shift+ctrl+v? Is there anything else that I can try to fix this problem. I've grown used to pressing shift+ctrl+v to paste now, and having to remember to press shift+Ins does slow me down :-?

---

### Post by nike984 on 2010-11-01
I have the same problem in 10.10. It's really annoying :(

---

### Post by Budoc on 2010-11-01
Hi,

When I posted this, I couldn't get on launchpad to check whether there were any bug reports filed for this. Since then I have been able to look, and I found [this]("https://bugs.launchpad.net/ubuntu/+source/gnome-terminal/+bug/630383"). So it seems that people are aware of this, despite the lack of posts on this forum, and hopefully it'll get fixed soon :)

---

### Post by drs305 on 2010-11-01
As an alternative (and even faster) can you paste the clipboard by highlighting with your mouse and then middle clicking in the terminal?

Note: I'm using 64-bit Maverick and the CTRL-SHIFT-V works as always...

---

### Post by Budoc on 2010-11-01
> **drs305 said:**
> As an alternative (and even faster) can you paste the clipboard by highlighting with your mouse and then middle clicking in the terminal?

Note: I'm using 64-bit Maverick and the CTRL-SHIFT-V works as always...

Hi,

I'm using a laptop without an external usb mouse, but I'm lead to believe that pressing both my left and right mouse buttons is equivalent to this. If that's the case, then middle clicking in the terminal does paste for me, whereas shift+ctrl+v does not.

---

### Post by Quackers on 2010-11-01
> **Budoc said:**
> Hi,

I'm using a laptop without an external usb mouse, but I'm lead to believe that pressing both my left and right mouse buttons is equivalent to this. If that's the case, then middle clicking in the terminal does paste for me, whereas shift+ctrl+v does not.

Same for me.

---

### Post by Cavsfan on 2010-11-01
> **drs305 said:**
> As an alternative (and even faster) can you paste the clipboard by highlighting with your mouse and then middle clicking in the terminal?

Note: I'm using 64-bit Maverick and the CTRL-SHIFT-V works as always...

Same here! :)

---

### Post by Traxster on 2013-03-23
ctrl + left click + right click (all at the same time) allowed me to paste in terminal from the clipboard. I am on 12.10

---

### Post by oldos2er on 2013-03-23
Old thread closed.

---


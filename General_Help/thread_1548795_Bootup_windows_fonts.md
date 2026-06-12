---
title: "Bootup windows fonts"
date: 2010-08-08
forum: General Help
---

### Post by d0.higgs on 2010-08-08
Hi,

I am using Ubuntu 10.04, and sometimes I just need the boot window (ie. a no gui environment through Ctrl+Alt+F?.)
My question is how to control the window fonts size?

Thanks

---

### Post by chopinhauer on 2010-08-09
> **d0.higgs said:**
> 
My question is how to control the window fonts size?


In the console you change font size by loading another font, e.g.:
```
setfont Uni2-TerminusBold20x10
```
See the directory /usr/share/consolefonts for a list of fonts and font sizes. Otherwise you can use a terminal emulator like **gnome-terminal**.

---

### Post by d0.higgs on 2010-08-09
Hi Chopinhauer,

I tried this:
```
setfont Uni2-Terminus12x6
```
Which is listed in my /usr/share/consolefonts/
but I got this error:
```
Couldn't get a file descriptor referring to the console
```

Any comment.

PS.
I want to change the font size when I use my box in a text mode.

---

### Post by The Cog on 2010-08-09
This might prove useful. Haven't tried it myself.
[http://linuxandfriends.com/2008/09/17/vga-modes-used-linux/](http://linuxandfriends.com/2008/09/17/vga-modes-used-linux/)

---

### Post by chopinhauer on 2010-08-09
> **d0.higgs said:**
> 
but I got this error:
```
Couldn't get a file descriptor referring to the console
```Any comment.


Did you run the command in the console (CTRL+ALT+F1) or in a terminal emulator?

---

### Post by d0.higgs on 2010-08-10
in an emulator, for testing purposes

---

### Post by chopinhauer on 2010-08-10
> **d0.higgs said:**
> in an emulator, for testing purposes
That is why it failed. The actions that 'setfont' takes to change the font don't work on a terminal emulator.

---


---
title: "i dont see the desktop icons..."
date: 2011-01-05
forum: General Help
---

### Post by Torombolo on 2011-01-05
i was playing with commands, trying to add some wallpapers, and suddenly... i dont anything on my desktop, nor can drag and drop, but when i open the desktop folder all is there... need some help 



Thanks you.

---

### Post by Dans564 on 2011-01-05
log out and log back in.

---

### Post by Torombolo on 2011-01-05
did that nothing, restarted, and Power Off and power on and nothing.

---

### Post by matt_symes on 2011-01-05
Hi

> i was playing with commands

What commands?

Kind regards

---

### Post by anystupidname1 on 2011-01-05
Here you go:
start gonf-editor
got to 
apps>nautilus>preferences

[IMG]http://i.imgur.com/448QE.jpg[/IMG]

I know for a fact that you can simply turn them on and off with a checkbox using ubuntutweak as well.
[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

P.S. Careful with that whole playing with them commands thing... :P

---

### Post by Torombolo on 2011-01-05
to be exact,  this one 

```
gconftool-2 —type bool —set /apps/nautilus/preferences/show_desktop false 
```

---

### Post by matt_symes on 2011-01-05
Hi

change to true.

```
gconftool-2 &#8212;type bool &#8212;set /apps/nautilus/preferences/show_desktop true
```

You stopped nautilus from drawing the desktop.

anystupidname1 shows how do change it from gconf-editor as well

anystupidname1: Love the name ;)

Kind regards

---

### Post by anystupidname1 on 2011-01-05
What they ^ said! :)

---

### Post by Torombolo on 2011-01-05
Worked like a charm thank you. now im going to play some more >.> jajajaja

---

### Post by Dans564 on 2011-01-05
> **Torombolo said:**
> Worked like a charm thank you. now im going to play some more >.> jajajaja

that is what it is all about... LOVE IT!

---


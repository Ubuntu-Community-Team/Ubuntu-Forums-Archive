---
title: "Pen tablet causes Save As dialog problem"
date: 2010-01-13
forum: General Help
---

### Post by Is Mise on 2010-01-13
This is kind of a weird bug, and I'm not quite sure where to file it at:


In GIMP and MyPaint, when I click on Save As with my Wacom Bamboo pen, none of the controls in the Save As dialog work. The buttons are highlighted when I hover over them, but can't be clicked with the pen, Wacom mouse, or my regular mouse.

If I click Save As using my non-tablet mouse, and the Wacom mouse is off the tablet, all the controls work fine, even when adjusted with the pen.

In MyPaint, this only happens the second time Save As is shown, and also affects the Brush Settings dialog.


I'm using Karmic 32-bit. Has anyone else experienced this problem?

---

### Post by Favux on 2010-01-13
Hi Is Mise,

Welcome to Ubunut forums!

It sounds like a core pointer confusion.

In Gimp in Edit > Preferences > Input Devices > Configure Extended Input Devices:

Are stylus, eraser, and cursor set to Screen and mouse to disabled?

---

### Post by Is Mise on 2010-01-13
Hi, Favux, thanks for the welcome.

Right now I have stylus and eraser set to Screen, and all the rest disabled. I had cursor set to Screen earlier, but I figured I didn't need to since the mouse isn't pressure sensitive and it works just like my regular mouse when it's set to disabled.

---

### Post by Favux on 2010-01-13
Hi Is Mise,

I've noticed if I've been messing around and there's a crash things won't work right in Gimp.  The Extended Input Devices will say things are set right but they aren't.  If I reset them and save it gets straightened out.  Did you have a crash in Gimp or with Gimp opened recently?

---

### Post by Is Mise on 2010-01-13
Nope, no crashes recently. I've also tried reinstalling Gimp and erasing the ~/.gimp-2.6/ folder, but it didn't help. I get the same problem on my laptop as well, which is also running Karmic.

When all extended input devices are set to disabled in Gimp the error doesn't happen, but then I don't get pressure sensitivity.

---

### Post by Favux on 2010-01-13
Huh.  That's sure sounding like a Gimp bug isn't it?  But it also affects MyPaint.  So something with Xinput?  Can't be linuxwacom because you're on the default 0.8.4-1 and it was working ok.

Let's see, there was a kernel update a few days ago and yesterday wasn't there a C library update?

---

### Post by Is Mise on 2010-01-13
Yeah, that's true. I haven't used my tablet in Gimp for a while, I think I was using Jaunty last time I did and I don't remember noticing the problem then.
I suppose I could try booting from an older kernel to see if that fixes it, although I just found a thread that seems to indicate it's a GTK problem: [http://www.mail-archive.com/gimp-developer@lists.xcf.berkeley.edu/msg19192.html]("http://www.mail-archive.com/gimp-developer@lists.xcf.berkeley.edu/msg19192.html")

---

### Post by Favux on 2010-01-13
Hi Is Mise,

Nice find.  lol, I was going to suggest posting on linuxwacom-discuss because Alexia is there sometimes and is a Gimp dev.  From what Alexia says it is a GTK problem and you're apparently stuck, at least as far as Gimp is concerned, because Gimp in Karmic needs the newer GTK with the bug to build.

---

### Post by Is Mise on 2010-01-13
Yup, I guess I'll have to live with it for now. :)
At least I found a workaround: if I bring up the dialog with the keyboard shortcut or with my non-tablet mouse everything works fine.

Thanks for the assistance, though.

---

### Post by TygerFish on 2010-09-30
The non-tablet mouse doesn't work for me, but the keyboard shortcut does!  Strange.  But whatever works...

---

### Post by Dan_Dranath999 on 2010-10-12
I'm using Gimp + wacom Bamboo in Lucid. Still getting dialog bugs when called from the tablet.

---


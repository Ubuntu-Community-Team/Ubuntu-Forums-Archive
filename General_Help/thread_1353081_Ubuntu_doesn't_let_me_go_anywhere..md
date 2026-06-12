---
title: "Ubuntu doesn't let me go anywhere."
date: 2009-12-12
forum: General Help
---

### Post by GroogFish on 2009-12-12
I can't access any of the system files as my admin. It says I am not allowed to access them because I don't have the proper privileges. It's getting on my last nerves, ubuntu shouldn't tell me what I can and can't do- It's ubuntu!

Anyone know how I can fix this? I'm trying to stick a font file into the usr/shared/fonts/truetype folder (I don't know if that's the exact path).

---

### Post by ST3ALTHPSYCH0 on 2009-12-12
are you moving with the terminal or file browser?

---

### Post by howefield on 2009-12-12
Have a read at this...

[https://wiki.ubuntu.com/Fonts#Manually](https://wiki.ubuntu.com/Fonts#Manually)

---

### Post by jollysnowman on 2009-12-12
As admin or root? There's a difference.

---

### Post by GroogFish on 2009-12-12
I've tried both admin and root. I haven't tried the terminal for this yet but I would really like to set it up so I don't have to look up the terminal commands every time I want to edit or add something.

---

### Post by ST3ALTHPSYCH0 on 2009-12-12
if you hit Alt+f2 the enter 
```
gksudo nautilus
```
it will open a root file browser.
you can copy the files in your standard file browser and paste them into the target folder in the root file browser.

---

### Post by NoaHall on 2009-12-12
What do you mean "admin and root"? Root has the superpowers. You should use "sudo" and "su".

---


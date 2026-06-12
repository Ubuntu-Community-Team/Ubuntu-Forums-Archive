---
title: "Auto-hide panel only shows up by hovering corner"
date: 2010-05-06
forum: General Help
---

### Post by orlox on 2010-05-06
I usually like having my panels auto-hide to take advantage of screen real-state...However, using lucid, the top panel only unhides itself when I hover over the top-left corner. This is very annoying, since it forces me to move the mouse to two different places before getting what I want...

gconf-editor keys for the panel don't include anything about this...Has anyone else been annoyed by this issue?? Any solutions??

Cheers!

---

### Post by tiato on 2010-06-20
I had this same issue with ubuntu 10.04 - turned out to be some setting in desktop wall compiz plugin. when i disabled it to go for the preferable cube i was able to unhide my top bar without going to the corners.

not sure this helps you out but disabling desktop wall worked for me

---

### Post by orlox on 2010-06-20
Precisely, the disabling of desktop wall solved it. Shouldnt this qualify as a bug?

---

### Post by tiato on 2010-06-21
I think so or a feature request as desktop wall doesn't actually have a setting to change this and going through gconf-editor it looks the same whether it's enabled or disabled.

It wouldn't be such a problem if desktop wall had the option to enable/disable this function as I do prefer desktop wall on the lappy since it doesn't have such a powerful gfx card but, like you, I can't stand going to the corners to unhide the taskbar.

---

### Post by sternschnupper on 2010-07-05
i had the same problem, and it was related to only one feature in the desktop wall plugin: the "Edge Flip DnD". unchecking this has my panel auto-un-hide perfectly again, letting me keep the rest of the desktop wall plugin.

thanks a lot for the hint, tiato!!!

---

### Post by andres.ordonez on 2011-05-25
I had the same problem, and it was related to TWO features in the desktop wall plugin: 

"Edge Flip DnD" 
"Edge Flip Pointer". 

Unchecking these has my panel auto-un-hide perfectly again.

---

### Post by ltn100 on 2011-06-06
> **andres.ordonez said:**
> I had the same problem, and it was related to TWO features in the desktop wall plugin: 

"Edge Flip DnD" 
"Edge Flip Pointer". 

Unchecking these has my panel auto-un-hide perfectly again.

Actually, for me it was just the "Edge Flip DnD" that was causing the problem.

---


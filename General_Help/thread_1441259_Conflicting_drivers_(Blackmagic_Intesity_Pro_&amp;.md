---
title: "Conflicting drivers (Blackmagic Intesity Pro &amp; Nvidia GTX270)"
date: 2010-03-28
forum: General Help
---

### Post by makkusu on 2010-03-28
Hello Forum,

I was unsure where to place this thread so if this belonged somewhere else, i'm sorry.

I have two cards: an Intesity Pro Capture card and a Nvidia GTX270 card.
My Nvidia card works fine, but when i install my capture cards drivers then during boot i get the message that it needs to boot in low-graphics mode due to misconfiguration.
Then my capture card works fine (i think), but im stuck with low-graphics.

anyone can help me get both drivers co-exist?

thanks in advance,
-Makkusu

EDIT: after some more trial and error, i manually build the drivers and reloaded them with modprobe blackmagic. its now working perfectly

---

### Post by larcho on 2010-08-10
Could you explain how you manually built the drivers ?

I have the same issue.

---

### Post by matiasw on 2011-01-25
I resolved this by setting vmallocs to 256M, as described [here]("http://ubuntuforums.org/archive/index.php/t-1004660.html").

---

### Post by calande on 2011-03-07
Hello, does the Blackmagic Intensity capture board work with VLC in HD using the HDMI input? Thanks!

---


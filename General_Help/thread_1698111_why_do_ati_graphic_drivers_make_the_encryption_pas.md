---
title: "why do ati graphic drivers make the encryption password screen so ugly?"
date: 2011-03-01
forum: General Help
---

### Post by pizztry on 2011-03-01
Is there a way I can get the clean screen back for when I enter the encryption password during boot? 

It was quite clean and nice before the drivers but now it just looks awful

---

### Post by Vaphell on 2011-03-01
not that i know what it looks like but i think it's because proprietary drivers don't support few features like kernel mode setting that is responsible for resolution detection and go with some pathetic lowres during bootup. At least that's what i see in case of ubuntu splashscreen - it's big, ugly and pixelated.

---

### Post by Veld on 2011-03-01
Does the screen look unfocused? I think this is the same problem I had. It got solved by lowering the resolution. Still have to figure out how to make the image fit the whole screen, though (right now I have huge black borders of unused space because the image doesn't fill the screen).

---

### Post by Vaphell on 2011-03-01
[http://www.webupd8.org/2010/10/script-to-fix-ubuntu-plymouth-for.html](http://www.webupd8.org/2010/10/script-to-fix-ubuntu-plymouth-for.html)

this reportedly helps with resolution during bootup, though i have no idea if it fixes OP's problem.

---


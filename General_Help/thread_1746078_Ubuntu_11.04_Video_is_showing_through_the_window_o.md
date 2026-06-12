---
title: "Ubuntu 11.04 Video is showing through the window on top."
date: 2011-05-01
forum: General Help
---

### Post by DBQ on 2011-05-01
Hi Everybody.

I recently upgraded to Ubuntu 11.04.  

I started having this problem. When I have a video running in Totem, and you put window over totem, the video shows through the window on top.  This happens with any video application.

Any ideas? Help is appreciated.

---

### Post by gabrielitos on 2011-05-02
Hi DBQ,

I experienced the same problem and I found a way to solve it, don't know if the most optimal but it's actually working.

In a terminal, execute 
```
gstreamer-properties
```

and in the second tab change the Plugin option in the "Default Output" to "X Window System - Without XV".

It was the same problem that I experienced with XGL some time ago, that is why I knew it. I hope this is useful for you.

---

### Post by DBQ on 2011-05-02
Thanks for the reply!  Unfortunately, this had no effect. 

I choose the option "X Windows System (No Xv)" (this is the closest thing that matches your suggestion.

Any other ideas?  This is really frustrating.

---

### Post by DBQ on 2011-05-02
Any ideas anybody?

---

### Post by alex@HPC6710b on 2011-05-03
Same problem here.
The suggestion of gabrielitos worked for me.

---

### Post by gabrielitos on 2011-05-05
I guess you have an ATI graphic card, like me.

Try to disable the propertary driver from the administration tool, that worked for me as well.

---


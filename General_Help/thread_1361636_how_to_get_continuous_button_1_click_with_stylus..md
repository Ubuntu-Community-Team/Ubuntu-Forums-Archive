---
title: "how to get continuous button 1 click with stylus."
date: 2009-12-22
forum: General Help
---

### Post by ulugeyik on 2009-12-22
I am having difficulty finding what to configure in order to get the touchpad/stylus combination behave as they did in the past.

I want it to act as if I am continuously pressing "button 1" (left button on most mice) when it is pressed and dragged. I was able to drag windows, draw using xournal etc before installing UNR, 9.10.

this is on the touchscreen of samsung Q1 Ultra using evtouch.

Thanks,

---

### Post by ulugeyik on 2009-12-22
Running "xev" when the stylus touches the screen it registers "ButtonPress" and "button 1", then when I keep it pressed it senses "motion", when I lift it "ButtonRelease" so it is, I think, getting the right commands but acting as if I kept the button pressed continuously.

---


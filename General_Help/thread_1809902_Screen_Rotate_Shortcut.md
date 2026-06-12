---
title: "Screen Rotate Shortcut"
date: 2011-07-22
forum: General Help
---

### Post by teejay17 on 2011-07-22
This is probably so easy, but I can't seem to find it anywhere. 
What shortcut does one use to rotate the screen? Is there a ctrl+alt+arrow key (*a la* Windows) equivalent?

---

### Post by realzippy on 2011-07-22
Open terminal,run:

```
xrandr -o left
``` 

(or "right" if you prefer)

..to get back:

```
xrandr -o normal
```

If this works,you can create a shortcut of your choice with

*xbindkeys*  ,see:

[http://ubuntuforums.org/showthread.php?t=79560&page=1](http://ubuntuforums.org/showthread.php?t=79560&page=1)

---

### Post by realzippy on 2011-08-22
Just cleaning up my subscribed threads.
Please set thread as solved (ThreadTools)...thanks

---

### Post by landstander on 2012-10-01
> **realzippy said:**
> Open terminal,run:

```
xrandr -o left
``` 

...


Unfortunately this method doesn't work any more in Kubuntu 12.04. Can any one confirm if this method still works in Ubuntu 12.04?

---


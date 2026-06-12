---
title: "terminal command to change sound?"
date: 2009-08-08
forum: General Help
---

### Post by manfrom3004 on 2009-08-08
I use a program called easystroke that lets me use gestures to control my desktop. In order to use a gesture, I need a terminal command that it needs to execute.
I want to set up two gestures that change my volume up and down, but I cant find a command that does that.

---

### Post by cosine352 on 2009-08-08
try
> amixer -c 0 sset PCM,0 60%

---

### Post by manfrom3004 on 2009-08-08
thx. is there any way to increase it relative to its current volume? like add 10% every time the command is used?

---

### Post by manfrom3004 on 2009-08-08
ok, i looked on the man page and figured it out. to increase by 10%,
> amixer -c 0 sset PCM,0 10%+


---

### Post by manfrom3004 on 2009-08-08
But, how can I control the volume that I control from the gnome-panel?

---

### Post by unutbu on 2009-08-08
```

amixer sset Master 10%+ 
```

---

### Post by manfrom3004 on 2009-08-08
Thanks a lot, but is there any way to get the notification to show up? The one that shows what your volume is at?

---

### Post by cosine352 on 2009-08-09
> alsamixer
this may help

---


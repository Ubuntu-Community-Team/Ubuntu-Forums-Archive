---
title: "Screen Upside Down and Inside Out"
date: 2010-11-20
forum: General Help
---

### Post by flood222 on 2010-11-20
I turned on my computer and the Ubuntu desktop is flipped upside down and inside out. I can still SSH in and ran a backup which is good but now I need to fix this. 
 
Where should I start? I dont know which logs to start checking or what to do. Assistance is appreciated.

---

### Post by flood222 on 2010-11-20
`metacity --replace`  seemed to do the trick.  (alt f2 to open run window)
 
Looks like it's compiz that was doing it.

---

### Post by linux18 on 2010-11-20
That is the strangest problem I've heard of yet, try

```
 rm $HOME/.config 
```

---

### Post by flood222 on 2010-11-20
Tried that, no dice.  Agreed though, really strange problem.

---

### Post by flood222 on 2010-11-20
Ok, so I had to change the default window manager in the gconf-editor to use metacity.  Now it uses that by default after a reboot.

I still don't know why compiz is flipping the screen inside out and backwards.  Talk about a PITA.

---


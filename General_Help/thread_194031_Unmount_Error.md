---
title: "Unmount Error"
date: 2006-06-10
forum: General Help
---

### Post by sauceboy23 on 2006-06-10
Unable to eject media. 

eject: unable to eject, last error: Invalid argument

This happens when I try to unmount my iPod. Anyone know whats up? (20 gig photo/color)

---

### Post by scxtt on 2006-06-10
how are you accomplishing this (terminal, right-click on desktop icon)?

---

### Post by taurus on 2006-06-10
Make sure no program is accessing it and you are not in the directory where you've mounted it...

---

### Post by sauceboy23 on 2006-06-10
I'm doing this from the desktop. I don't think I'm in the directory when I'm unmounting it, and i always quit Amarok...any ideas?

---

### Post by scxtt on 2006-06-10
do a 'pwd' from the terminal you're in to see what directory you're in ... and read the man page on fuser ($:> man fuser), that should give you a way to see "who" is accessing a filesystem ...

---

### Post by InsanePenguin08 on 2006-06-11
I've always gotten this error, as well, and from what I can find there really isn't anything to be done about it, and it doesn't seem to do any damage to the iPod.

---

### Post by kuja on 2006-06-11
One thing that's worth trying is opening a terminal and typing ```
sudo eject [insert device name here]
```

If that doesn't work, ```
fuser -c [insert device name here]
``` should tell you what's using it... if there aren't a bunch, try killing them ```
kill [number]
```

---


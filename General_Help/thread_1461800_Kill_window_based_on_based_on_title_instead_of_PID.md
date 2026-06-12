---
title: "Kill window based on based on title instead of PID?"
date: 2010-04-24
forum: General Help
---

### Post by drewsus on 2010-04-24
Hello All!
I am working on a set up, and I like to be able to toggle compiz on and off, or toggle dualscreen on and off. The thing is, I also have conky on my desktop as well as a terminal window embedded in my desktop (that requires compiz). 
So, when I turn comiz off, or resize my desktop, I want to be able to reposition conky/embedded-terminal and the terminals position is relative to my conky position and the size of my virtual desktop.

I can do this all fine, except that to reposition the terminal I need to kill it then reopen it. But if I kill gnome-terminal it kills ALL gnome-terminals instead of just my embedded one. **How can I specifically close my embedded one and leave any others untouched? Lets say that the title of my embedded terminal is "trans777"**
Also, the trans777 titled gnome-terminal will be killed when compiz is not running.

Any ideas?

Drewsus

---

### Post by drewsus on 2010-04-24
Figured it out. 
Using the package wmctrl I can close the window by title using: 
```
wmctrl -c "trans777"
```
Furthermore, I don't need to close the terminal and reopen it, I can simply reposition and resize it using: 
```
wmctrl -r <WIN> -e <MVARG>
```

For those interested, check this page: [wmctrl]("http://tripie.sweb.cz/utils/wmctrl/")

---


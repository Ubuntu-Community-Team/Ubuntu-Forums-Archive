---
title: "Use wmctrl to unmaximize a window - not toggle"
date: 2010-09-01
forum: General Help
---

### Post by finny388 on 2010-09-01
Hello,

To mimick aero snap and some of my own ideas I'm using wmctrl to position and resize windows. for example:```
wmctrl -r :ACTIVE: -e 0,0,0,674,768
```

But if the window is maximized, the command doesn't work. I have to unmaximize, then use the command.

I can't use toggle or else an unmaximized window will maximize and again the command won't work.

How do I use wmctrl to position/resize a window whether it is max'ed or not?

thanks

---

### Post by finny388 on 2010-09-04
I've read the man page and don't see an answer

:o

---

### Post by finny388 on 2010-09-07
maybe I just ask elsewhere?
:)

---

### Post by finny388 on 2010-09-09
^

---

### Post by finny388 on 2010-09-13
[-o<

---

### Post by finny388 on 2010-09-13
wow, what a quiet thread

I finally figured it out:
```

wmctrl -r :ACTIVE: -b remove,maximized_vert; wmctrl -r :ACTIVE: -b remove,maximized_horz; wmctrl -r :ACTIVE: -e 0,0,0,674,768
```

---

### Post by wannabegeek on 2011-01-28
thank you very much....was having same problem and didn't see it in man pages....

good work !

---

### Post by pclausen on 2011-11-05
tnx from me as well. I now have shortcuts making my windows fill the left (<SUPER>+LeftArrow) or the right (<SUPER>+RightArrow) screen-half. 

Example: ( [FONT="Courier New"]/usr/local/bin/win_active_right.sh[/FONT] )
```

#!/bin/sh

wmctrl -r :ACTIVE: -b remove,maximized_vert
wmctrl -r :ACTIVE: -b remove,maximized_horz
wmctrl -r :ACTIVE: -e 1,510,21,510,700

```

you have to play around a bit with the last 4 numbers till it fits your screen correctly.

---


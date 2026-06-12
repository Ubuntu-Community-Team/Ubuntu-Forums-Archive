---
title: "Xbindkeys"
date: 2009-09-02
forum: General Help
---

### Post by pedrom169 on 2009-09-02
i currently have xmacro and xbindkeys set up so when i press f1 it goes to a co-ordinate on the screen.

I was wondering if there is anyway to be able to press for example f7

to make it

click a co-ordinate
type a few words i set and then press enter?

Thanks

---

### Post by PGScooter on 2009-09-02
this should be possible with xmacrorec2, but it is currently broken. See the following bug for progress on fixing it:

[https://bugs.freedesktop.org/show_bug.cgi?id=20500](https://bugs.freedesktop.org/show_bug.cgi?id=20500)

alternatively you could try to figure out the commands yourself and just make a text file with the commands and play it with xmacro

---

### Post by pedrom169 on 2009-09-02
is there any website that shows the different variables for xmacro?

---

### Post by PGScooter on 2009-09-02
I would suggest looking up scripts for xmacro (on google?) and getting the varibles from there.

---

### Post by unutbu on 2009-09-02
If you install the xdotool package, then you can move,click,type with commands like
```

xdotool mousemove 500 500
xdotool click 1
xdotool type "Hi pedrom169" 
```

You can wrap that into a script and  hook it up to F7 with xbindkeys.

---

### Post by pedrom169 on 2009-09-02
how would i attach such thing to xbindkeys? (sorry)

---

### Post by unutbu on 2009-09-02
Save this in ~/bin/f7.sh:
```

#!/bin/bash
xdotool mousemove 500 500
xdotool click 1
xdotool type "Hi pedrom169"

```
Make it executable:
```

chmod +x ~/bin/f7.sh
```

Test that it works by running
```

f7.sh
```

After installing the xbindkeys package, put this in ~/.xbindkeysrc
```

"f7.sh"
  F7
```

Then run the xbindkeys program in the background:
```

xbindkeys &
```

If it works, then you can add xbindkeys to the list of commands GNOME runs when you log in: System>Pref>Sessions. 

Note: I've tried this out, and it works the first time you press F7. But then you must move and click the mouse in another window before F7 will work again. At least that has been my experience so far... I only installed xbindkeys half an hour ago.

---

### Post by pedrom169 on 2009-09-02
that is brilliant!

do you know if it is possible to tell xdotool to paste something that in your i have copied?

---

### Post by unutbu on 2009-09-02
Yes, I think that is possible.
In general, Ubuntu programs use one of two clipboards: The X clipboard or the GNOME clipboard.

If you select text with the mouse and click the middle mouse button to paste, then you are using the X clipboard. You can generate the middle mouse button click with the command "xdotool click 2"
```

#!/bin/bash
xdotool mousemove 500 500
xdotool click 2
```


If you select text with the mouse and press Ctrl-v to paste, then you are using the GNOME clipboard. You can generate the Ctrl-v with the command xdotool key "ctrl+v" :

```

#!/bin/bash
xdotool mousemove 500 500
xdotool click 1
sleep .1
xdotool key "ctrl+v"
```

By the way, I managed to fix the slight bug I was experiencing before:
For whatever reason (I do not know), I find putting a short sleep in the script 
makes the problem go away.

---

### Post by pedrom169 on 2009-09-02
you are an absolute star.

one last thing.

How would i perform a return press?

I have tried

xdotools key "return"
xdotools key "enter"

Thanks

---

### Post by unutbu on 2009-09-02
```
xdotool key "Return"
``` :)

---

### Post by pedrom169 on 2009-09-02
haha. damn capitals. your a star pal! if i could thanks i would. well that didnt take long and i have learnt something.

Thank you again pal!

---


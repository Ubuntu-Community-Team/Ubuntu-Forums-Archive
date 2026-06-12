---
title: "Missing windows boarders?"
date: 2010-06-03
forum: General Help
---

### Post by schwabdale on 2010-06-03
I don;t know what I did, but I am missing my windows boarders. 
Please help!

---

### Post by WorMzy on 2010-06-03
Press Alt+F2, then run ```
metacity --replace
```

That should get your borders back for now, but does this behaviour occur every time you boot up?

---

### Post by schwabdale on 2010-06-03
Yes, every time I boot up

---

### Post by schwabdale on 2010-06-03
after I run the metacity --replace command, it quickly pops a border on, then disappears. I also noticed I lose keyboard functionality here and there.

---

### Post by WorMzy on 2010-06-03
Can you open a terminal, then run the command in there, it should post any error messages which are causing it to abruptly exit. Post them here.

Also, try running gtk-window-decorator --replace, (if you have compiz installed) see if that fares any better.

---

### Post by schwabdale on 2010-06-03
no errors post. Should I install compiz?

---

### Post by Craig Magner on 2010-06-03
Compiz might give you some luck, try that

---

### Post by varunendra on 2010-06-03
What if you boot in safe graphics mode?

---

### Post by WorMzy on 2010-06-03
What, no errors at all, it just silently exits and returns you to a terminal prompt? That is very unusual. You can try installing compiz (and libdecoration0, for gtk-window-decorator) if you want. First I'd try reinstalling metacity and metacity-common, just in case something became corrupted.

---

### Post by schwabdale on 2010-06-03
Thanks all for the quick responses. Installing compiz worked.

---

### Post by varunendra on 2010-06-03
> **schwabdale said:**
> Thanks all for the quick responses. Installing compiz worked.

Knowing the exact reason would have been better though, I think you can mark the thread as [solved] now.

---

### Post by WorMzy on 2010-06-03
Happy to help. But has it fixed it so you get a window decorator after booting?

You may need to run gconf-editor and edit the keys at ```
/desktop/gnome/applications/window_manager/default
``` and/or ```
/desktop/gnome/session/required_components/windowmanager
```

Set them both to /usr/bin/compiz if necessary.

You may also need to enable the window decorator plugin in Compiz (by installing and running ccsm), and setting the command to ```
gtk-window-decorator --repalce
```

---


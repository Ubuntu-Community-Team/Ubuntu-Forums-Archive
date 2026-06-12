---
title: "Shiretoko won't start at all."
date: 2009-08-11
forum: General Help
---

### Post by ToastyMallows on 2009-08-11
Recently I updated to Firefox 3.5 or "Shiretoko".  It worked fine but after a reboot one day it stopped working.  When I open it from the Applications menu it says "Starting Shiretoko..." in the panel for about 7 seconds and then it doesn't open anything.

Any one having the same problem? Solutions?

---

### Post by michy99 on 2009-08-11
Try starting it from a terminal to see what error messages you get.```
firefox-3.5
```

---

### Post by ToastyMallows on 2009-08-11
> **michy99 said:**
> ```
firefox-3.5
```

This made it work but I don't wanna start it from the terminal everytime.  What might be wrong?

---

### Post by nothingspecial on 2009-08-11
Go to system > prefrences > main menu

Find your menu entry for firefox or shiretoko or whatever it is.

Click on the propeties tab.

The command should read ```


firefox-3.5 %u
```

Does yours?

---

### Post by michy99 on 2009-08-11
Right click on 'Applications' in the upper left corner and choose Edit Menus. Find the entry for Shiretoko and check the Properties. See what command it is running.

---

### Post by kn100 on 2009-08-11
If you want to update your 3.0 to 3.5 with the official firefox branding and the such, use ubuntuzilla (google for it)

---

### Post by ToastyMallows on 2009-08-11
> **nothingspecial said:**
> Go to system > prefrences > main menu

Find your menu entry for firefox or shiretoko or whatever it is.

Click on the propeties tab.

The command should read ```


firefox-3.5 %u
```

Does yours?

Ah see mine was only

```
 firefox %u 
```

I dunno why but that was the problem, thanks everyone.

---


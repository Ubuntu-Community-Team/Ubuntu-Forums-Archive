---
title: "NX (nomachine) from Mac - capture alt-tab"
date: 2010-06-11
forum: General Help
---

### Post by ivarley on 2010-06-11
Howdy. I'm logging into a remote Ubuntu box from my Mac via NX, and almost everything works great. However, I can't find any way to capture the alt-tab keyboard combination (or, command-tab) for app switching. All the individual keys register with ubuntu, but when pressed together, Mac OS captures it first. Is there any way to fix this?

Thanks!
Ian

---

### Post by johnburbridge on 2010-09-06
Same issue here... I'm searching high and low for this but haven't found a solution yet.

---

### Post by johnburbridge on 2010-09-06
Found this very helpful page that describes the solution:

[http://stateless.geek.nz/2005/06/27/nx-osx-and-the-alt-key/](http://stateless.geek.nz/2005/06/27/nx-osx-and-the-alt-key/)

Turns out the issue isn't on the Ubuntu side but with X11 on the OSX side. The solution is pretty simple though.

On your mac, create a .Xmodmap file in your home directory with the following:
```
 
keycode 66 = Alt_L
clear Mod1
add Mod1 = Alt_L Alt_R

```

Now quit any X11 sessions you might have, relaunch your NX client and voilá!

---


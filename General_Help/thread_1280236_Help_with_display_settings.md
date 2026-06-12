---
title: "Help with display settings"
date: 2009-10-01
forum: General Help
---

### Post by Adrenochrom3 on 2009-10-01
Alrighty, i installed ubuntu on my new laptop, and im having some problems with the display. i have a 1366:768 res. when i restart my computer, these are the problems im having:

1: the display either shrinks back to a 1024:768 res, or
2: the icons on my panels are in places they shouldn't be, and it just makes my whole desktop look ugly and out of place.

what are some things i can do to maybe fix these problems?
 
also, i want to add a launcher onto cairo-dock that launches nautilus with root access. whats the run command for that?

---

### Post by undecim on 2009-10-01
Not sure about the resolution, but to launch nautilus with root access is not recommended--It makes it really easy to break your computer. If you still want to, though "gksu nautilus" will do it.

---

### Post by kayvortex on 2009-10-02
If your resolution isn't available in System -> Preferences -> Display, then you'll need to install drivers for your graphics card. Type:
```
lspci
```
to find out your card details if you don't already know. I probably can't help you install the actual drivers, but there'll be plenty of info around here, or elsewhere on the tubes, to do that.

---

### Post by Adrenochrom3 on 2009-10-03
well no see when i first went to the display settings, and set up my res, i clicked detect monitor. and it showed my res in the drop bar, and when i restart it stays at the res i put it on. its just when i restart, the icons at the top right and my recycling bin at the bottom right arent where they should be, they move more to the center of the screen, and messes the whole look of my computer up.

---

### Post by akakingess on 2009-10-03
Wanted to remove a post, misread the OP.

---

### Post by kayvortex on 2009-10-03
> well no see when i first went to the display settings, and set up my res, i clicked detect monitor. and it showed my res in the drop bar, and when i restart it stays at the res i put it on. its just when i restart, the icons at the top right and my recycling bin at the bottom right arent where they should be, they move more to the center of the screen, and messes the whole look of my computer up.

Right, ok, sorry. Could you post some info up anyway: I'll have to do some digging around in order to (try) to help. I'd probably recommend adding some stuff to your xorg.conf file, but it *might* not work (since xorg.conf seems to be used less than in previous ubuntu versions). For now, could you please post he contents of the file "/etc/X11/xorg.conf", the output of lspci (or your graphics card make and vendor if you know it), and if you've done anything with the display (like install proprietary graphics drivers).

Edit: some useful info [here]("https://wiki.ubuntu.com/X/Config/Resolution#Setting%20xrandr%20changes%20persistently") -- basically, you *can* add some things to xorg.conf to make your resolution permanent (although the fact that you changed them already in Preferences -> Display and they didn't stick could suggest something odd is happening). Anyway, post the xorg.conf file and I'll tell you what to add.

---

### Post by Adrenochrom3 on 2009-10-05
ok check your messages

---


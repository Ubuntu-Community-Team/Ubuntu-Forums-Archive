---
title: "Draw desktop icons at launch with Nautilus in Openbox?"
date: 2011-03-07
forum: General Help
---

### Post by migel_wimtore on 2011-03-07
Hello. I am using Openbox, i would like Nautilus to handle the desktop, which it does nicely, but i would like it so it draws the desktop at startup. 

So far the only way i have managed to do this is by adding "nautilus &" to the "autostart.sh", however, this, of course, launches an instance of the nautilus file browser.

Can anyone help me to get Nautilus to draw the desktop automatically at startup without having to first launch the file manager?

Thanks.

---

### Post by kerry_s on 2011-03-07
nautilus -n &

---

### Post by migel_wimtore on 2011-03-07
Hey, spot on.

Thanks.

I had been digging about on the net and tried a few intuitive command, like nautilus --desktop &, but hadn't though to actually consult nautilus help. 

Lesson learned.

---


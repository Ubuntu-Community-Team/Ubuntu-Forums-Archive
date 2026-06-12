---
title: "Problem with nautilus? Folders jumping around"
date: 2010-05-29
forum: General Help
---

### Post by jerome1232 on 2010-05-29
Okay so I'm having a problem with nautilus, whenever a program calls up the smaller nautilus window, the list of folders jumps around constantly making it impossible to select a specific directory and/or file.

It mainly seems to happen when I browse into my Videos folder, although I've seen it happen in /dev (using handbrake) (using gimp however didn't have this issue in /dev, although it did in my Videos folder)

---

### Post by nhasian on 2010-05-29
is that only when you use the mouse?  can you select folders with the tab and arrow keys?

---

### Post by drs305 on 2010-05-29
Moved from ABT to General as requested.

---

### Post by jerome1232 on 2010-05-29
I can use the keyboard to select folders but it's still the same thing, the folders are just jumping everywhere.

I tried to upload a short clip of it, seems I most drop the quality forums won't allow a tar over 900 kbs.

---

### Post by dino99 on 2010-05-29
reconfigure it or remove/purge & reinstall

---

### Post by jerome1232 on 2010-05-29
Running a simulation apt-get purge nautilus wants to remove gnome-session as well, you think that's safe for my current session?

---

### Post by jerome1232 on 2010-05-29
Okay so I just reconfigured it using (dpkg-reconfigure nautilus), and that seems to have solved the issue, so I am guessing a setting I changed must have been causing it somehow.

Thanks for the tip.

---


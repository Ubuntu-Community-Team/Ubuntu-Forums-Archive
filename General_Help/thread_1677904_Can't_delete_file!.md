---
title: "Can't delete file!"
date: 2011-01-29
forum: General Help
---

### Post by MachintoshCJ on 2011-01-29
[FONT=monospace]I tried "[/FONT]gksudo nautilus", and it didn't work! When the root window pops-up, it isn't there! I would like to delete this annoying file so that i can see my whole desktop! Will you help me! :mad:

---

### Post by howefield on 2011-01-29
With your nautilus window open, press Ctrl + H to view hidden files, can you see your file now ?

---

### Post by MachintoshCJ on 2011-01-29
> **howefield said:**
> With your nautilus window open, press Ctrl + H to view hidden files, can you see your file now ? Sadly No! I mean in the desktop file! I CAN SEE THE FILE ON THE DESKTOP. BUT WHEN I OPEN NAUTILUS, THERE IS NOTHING ON THERE! EVEN WHEN I TRY CTRL + H I STILL DON'T SEE IT:mad:

---

### Post by Joeb454 on 2011-01-29
Try clicking your desktop background, to bring focus to it, then pressing Ctrl+R to refresh the folder.

If that still doesn't work, post the output of ```
ls -la ~/Desktop
``` so we can see exactly what's going on :)

---

### Post by AlphaLexman on 2011-01-29
Make sure the 'file icon' isn't part of your background image.

That is a common prank.

---

### Post by MachintoshCJ on 2011-02-05
Thanks alot, but the file is still there!

---

### Post by 3rdalbum on 2011-02-05
In the root file browser, navigate to /home/(your username)/Desktop/ - don't just click on the Desktop bit in the sidebar as that will take you to Root's desktop.

---

### Post by AlphaLexman on 2011-02-06
It would still **REALLY** help us help you if we could see the output of:> **Joeb454 said:**
> ```
ls -la ~/Desktop
``` so we can see exactly what's going on :)in [code ] tags please!

---


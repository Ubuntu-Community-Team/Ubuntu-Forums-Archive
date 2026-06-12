---
title: "Is there a way to make screensaver aware of mplayer?"
date: 2004-10-23
forum: General Help
---

### Post by snowx1000 on 2004-10-23
It is annoying to have to remember to stop my screensaver before watching a movie (if I dont screensaver goes over movie).  Is there away to make the screensaver aware of when I am playing a movie, or an mplayer option?

---

### Post by cseg on 2004-10-23
Here's my command-line solution:

mplayer ()
{
    xscreensaver-command -exit;
    clear;
    /usr/bin/mplayer -vo xv "$@";
    xscreensaver -no-splash &
}

Put this in .bashrc.

Then when you start mplayer, it will automatically kill your screensaver.

---

### Post by snowx1000 on 2004-10-23
Thanks!  Will the screensaver come back on when I exit?

---

### Post by snowx1000 on 2004-10-23
oh wait, that last command probably starts it up, other question would be if this would apply to running it from an icon and not directly from console?

---

### Post by cseg on 2004-10-23
I you made a shell script (mplayer-wrapper.sh) instead of a shell function, I think you should be able to run it from an icon.

--- begin mplayer-wrapper.sh ---
#!/bin/sh
 xscreensaver-command -exit;
clear;
/usr/bin/mplayer -vo xv "$@";
xscreensaver -no-splash &
--- end mplayer-wrapper.sh ---

After creating this file, run

   chmod +x mplayer-wrapper.sh

to make it executable.  Then I think you can just refer to it in your icon definition.

---

### Post by Vulc on 2004-10-23
you can go to preferences > misc > stop xscreensaver

---


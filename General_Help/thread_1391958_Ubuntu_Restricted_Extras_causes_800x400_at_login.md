---
title: "Ubuntu Restricted Extras causes 800x400 at login"
date: 2010-01-27
forum: General Help
---

### Post by JosephWheatley on 2010-01-27
Ubuntu Restricted Extras affects the screen resolution on login and with each new reboot. 

I have to log out and in again to restore 1024x768 to get out of 800x400

I need the Restricted Extras to play DVDs so uninstalling it solves the resolution issue but leaves me unable to play DVDs.

---

### Post by MaindotC on 2010-01-27
This package has no affect on your video resolution or video module so it is not the issue regardless of whether or not the problem seems to only happen when that package is installed.  Now, in order to play dvd's just add the [Medibuntu repository](https://help.ubuntu.com/community/Medibuntu) and install the package libdvdcss2.

---

### Post by JosephWheatley on 2010-02-15
Thanks for your quick response.

Medibuntu has sorted this out.

At first I uninstalled Ubuntu Restricted Services and the resolution at first Log-in was back to normal. So I re-installed it to prove to myself that the resolution issue was coinciding with this installation - and so it was!

I now have an issue with the pitch of playback sound being slightly too high but I'm pursuing this in other threads.

---


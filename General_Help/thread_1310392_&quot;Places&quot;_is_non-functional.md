---
title: "&quot;Places&quot; is non-functional"
date: 2009-11-01
forum: General Help
---

### Post by mark92691 on 2009-11-01
I took a hard crash (i.e., without any warning, the screen instantly went totally black, and then the power-on boot sequence commenced) while working in 9.10, and, when I came back up again, the desktop was blank (should contain a few folders and documents), and the [Places] menu entry is completely non-functional.  When I select anything under [Places], I get a "wait" icon for ten seconds or so, and then control returns to the standard mouse pointer.  No window opens with any requested "place."

I can launch and operate applications, so the file system must be more-or-less intact.

TIA for any ideas on how to recover the desktop and get the [Places] menu entry working again,

Mark

---

### Post by absolutezero1287 on 2009-11-01
Have you tried reading the logs in /var/log to see what happened?

If all else fails and you can't fix the problem then get an ubuntu live CD and use apt-on cd to save your config and reinstall.

Tips: Always use a a seperate /home partition

---

### Post by mark92691 on 2009-11-03
Looks like "nautilus" is broken.  There's a file named /var/log/apport.log.1 with lines such as:

apport (pid 1999) Sun Nov  1 15:49:42 2009: executable: /usr/bin/nautilus (command line "nautilus")
apport (pid 1999) Sun Nov  1 15:49:42 2009: this executable already crashed 2 times, ignoring

And the above pair of lines repeats several times, each with a different pid and a longer command line, such as:  "nautilus --no-desktop computer:"

I can see the files that should be showing on the Desktop by using Terminal and the "ls" command, but they don't actually show up on the Desktop.

Mark

---


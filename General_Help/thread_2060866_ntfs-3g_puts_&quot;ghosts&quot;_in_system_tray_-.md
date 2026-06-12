---
title: "ntfs-3g puts &quot;ghosts&quot; in system tray - ???"
date: 2012-09-21
forum: General Help
---

### Post by spamhog on 2012-09-21
I have one data partition via ntfs-3g (mounted auto or manually) and all works fine. however...

[B]PROBLEM
IN LXDE AND GNOME, WHEN NTFS-3G IS ACTIVE,
4 EMPTY ICON PLACES ARE OCCUPIED IN THE SYSTEM TRAY.[/B]

I see them pop up there in succession after the desktop is first rendered.

If I modify fstab not to auto-mount the NTFS data partition, the ghost icons aren't there. If I mount a NTFS partition manually, they appear.

All four are inactive and invisible, no amount of right/left clicking causes them to do anything.

I don't know why, and why there are 4 - but my HD has 4 primary partitions: Window system NTFS, main data NTFS, mounted via ntfs-3g, Linux A ext4, Linux system B ext4, no /home, no swap (quite deliberately).

Things in the systray are usually there to introduce hooks to actions, I don't know what, why etc, and don't like ghosts anyway connected to partitions (if that's what it is),

[B]QUESTIONS
- Did anyone experience this?
- Should I worry?
- Can I stop it from happening?[/B]

Thank you in eager anticipation!

---

### Post by marinara on 2012-09-21
do the ghosts go away when rebooting?  if they do, i belive they are an lxpanel bug.  should be fixed for 13.04

---


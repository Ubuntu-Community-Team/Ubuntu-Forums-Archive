---
title: "Why would it boot into tty1?"
date: 2009-08-06
forum: General Help
---

### Post by muteXe on 2009-08-06
Switched on my laptop last night and it booted into TTY1 for some reason.  I pressed alt+ctrl+F7 and got back to my brown log-in screen and everything was fine.
I'm curious why it has started doing this?
Thanks.

---

### Post by muteXe on 2009-08-06
Forgot to mention that I'm dual-booting with slackware, but can't see why that would matter.

---

### Post by dcstar on 2009-08-07
> **muteXe said:**
> Forgot to mention that I'm dual-booting with slackware, but can't see why that would matter.

If your different OS's use totally different filesystems then yes, otherwise one could have corrupted the other.

---

### Post by teryowen on 2011-01-07
Dont mean to revive an old thread but im having the exact same problem, except that when I click ctrl alt f7, its frozen at the startup script:

A few statment with [ OK ] at the end (4 to be exact)
the last one is "* Setting sensors limits  [ OK ]"

By the way this is 10.10, on a dell XPS14 brand new. it booted up the first time just fine, then when i edited the default number entry for the grub menu to have default for windows 7, changed it from 0 to 4.

Then when I rebooted i selected the ubuntu entry and i got tty1 as described above.  

Any help would be greatly appriciated, thanks.

EDIT:

Just wanted to add something I noticed. When I click ctrl alt f7, at the top it says:

"(process:416): GLib-WARNING ***: getpwuid_r(): failed due to uknown user id (0)"

---


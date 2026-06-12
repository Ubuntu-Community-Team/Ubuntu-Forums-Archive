---
title: "Read-Only"
date: 2009-10-23
forum: General Help
---

### Post by Elfo33 on 2009-10-23
I'm running Karmic, and my system goes read-only at times.  As in, all items I try to access within my home folder are read-only.  I cannot edit documents until I reboot, I cannot make bookmarks in Firefox, etc.

I have not identified any program that seems to make this happen with regularity, does anyone have a lead on what may be happening?

---

### Post by alphaniner on 2009-10-23
Have you checked your logs (/var/log) after things become read-only?  I'm no authority, but I'd say debug, dmesg, kern.log, and sys.log would be good places to look.

You can view them in the terminal, or use the Log Viewer under System -> Administration.

If you post the bits from the log from around the time things got hairy, someone may be able to help you figure out what's going on.  Don't forget to use code tags!

---


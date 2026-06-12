---
title: "breezy only boots in text mode"
date: 2006-05-04
forum: General Help
---

### Post by toniti on 2006-05-04
My ubuntu only boots to text mode. I would like to get the gnome interface back.

Here's what I did:
I wanted to update glib to 2.8.3. Installed from source but it didn't start working. It said something like "the glib versions do not match." something like modprobe answered 2.8.3 as current version and something else answered 2.0.x (i don't remember). 

Then I went to that package management tool and removed the glib package that was listed as installed there. Then I noticed that some of the options got lost in my start menu. I saw samo more errors and then decided to reboot. When  the reboot was done my pc was in text mode.

I have tried to (re)install some packages with aptitude. Didn't help(maybe wrong package names).

When I type in "startx" I get an error saying something like can't access /home/<myname>/.Xsession . When I checked there was no such file.

The computer is a IBM laptop, it took me some days to get everything working so I don't want to reinstall it all again. Least not before the Dapper release.

---

### Post by harishg on 2006-05-04
Did you try to use the recovery mode.It might help.

---


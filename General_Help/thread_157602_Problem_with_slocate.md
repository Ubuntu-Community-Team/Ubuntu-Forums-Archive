---
title: "Problem with slocate"
date: 2006-04-09
forum: General Help
---

### Post by Brian031168 on 2006-04-09
Trying to install slocate (not sure why it isnt already installed) I get the following error:

> Unpacking slocate (from slocate_2.7-4_i386.deb) ...
Removing `diversion of /etc/cron.daily/find to /etc/cron.daily/find.notslocate by slocate'
dpkg-divert: rename involves overwriting `/etc/cron.daily/find' with
  different file `/etc/cron.daily/find.notslocate', not allowed
dpkg: error processing slocate_2.7-4_i386.deb (--install):
 subprocess pre-installation script returned error exit status 2
Errors were encountered while processing:
 slocate_2.7-4_i386.deb


Any idea what I can do to correct this?

TIA

---

### Post by mlind on 2006-04-09
backup /etc/cron.daily/find and then remove it.
then try to install slocate .deb.

---

### Post by Brian031168 on 2006-04-09
Thanks a lot for the quick reply mlind, that fixed it. Nice and easy when you know how.

---

### Post by Ludwin on 2006-10-22
I just came over this post after making a search en slocate. I had installed ubuntu-desktop after initially having installed xubuntu. I had the same problem, because of a slocate beta package that I could not remove from the configuration. Now it is fixed. Thanks!

---


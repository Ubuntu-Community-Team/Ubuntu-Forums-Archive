---
title: "Fresh install + Ramlog = read-only root filesystem"
date: 2011-08-11
forum: General Help
---

### Post by Ranko Kohime on 2011-08-11
Now this really has me confused.  I've previously had a Xubuntu 11.04 system running without hiccups with Ramlog, but this new one refuses to do so.

After installing, everything works fine until I install Ramlog, then reboot.  Upon starting up I get a GDM warning that /var/lib/gdm/.ICEAuthority is not accessible.

My home folder is encrypted, and of course GUI login is impossible, so entering the terminal mode, I poke around, and, apparently the root filesystem is read-only.

Booting into the install CD, the entire file system is read-write, and I can make whatever changes I wish.

Hardware is a Lenovo E420, with an 80GB Intel SSD, 4GB RAM.

---

### Post by Ranko Kohime on 2011-10-08
Bump.  Still would like to solve this one.

---

### Post by bamdad.khan on 2012-11-10
hi,

i'm on 12.04 and i have ramlog installed, but i haven't seen anything like this, although ramlog always gives me an error in the boot messages, and it's never running: even though it creates /var/log.hdd, it doesn't seem to be hardlinked to /var/log.

my advice is to stay away until a new version comes out, it's clearly buggy as hell.

i'm planning on creating a more simple implementation (as a clean upstart service) that also starts early in the boot process and syncs the /var/log tmpfs back to the disk on shutdown, but doesn't create any links or stuff like that. i can post it here or put it on github if you're interested.

bamdad

---


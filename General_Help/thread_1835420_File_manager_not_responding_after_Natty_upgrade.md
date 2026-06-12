---
title: "File manager not responding after Natty upgrade"
date: 2011-08-29
forum: General Help
---

### Post by davelosm on 2011-08-29
Hi all,

I've just done an upgrade to Natty, and gotten rid of Unity, running Ubuntu classic from login. I've just booted up and none of my folders are coming up, home, downloads etc. On gnome-do, when I type downloads or something, the icon is a stop sign, maybe suggesting a permissions issue but I have no idea, I'm still pretty new to this.

Anyone got any ideas? Would be much appreciated.
Dave

---

### Post by ajgreeny on 2011-08-29
> **davelosm said:**
> Hi all,

I've just done an upgrade to Natty, and gotten rid of Unity, running Ubuntu classic from login. I've just booted up and none of my folders are coming up, home, downloads etc. On gnome-do, when I type downloads or something, the icon is a stop sign, maybe suggesting a permissions issue but I have no idea, I'm still pretty new to this.

Anyone got any ideas? Would be much appreciated.
Dave
Was this a clean install or a distro upgrade with the update-manager?

Did you actually uninstall unity, and if so did you check what else was also uninstalled at the same time?

Do you have a separate /home partition, and if this was a clean install, was it set to be /home in fstab with the /home mountpoint?

What do you see if you start nautilus in terminal?

---

### Post by davelosm on 2011-08-29
It was a distro upgrade. No I didn't uninstall Unity, just using the session manager at login.

nautilus in the terminal gives me this:

Gtk-ERROR **: GTK+ 2.x symbols detected. Using GTK+ 2.x and GTK+ 3 in the same process is not supported
aborting...
Aborted


Thanks for the help

---

### Post by dino99 on 2011-08-29
clean the cache: clean, autoclean, autoremove

you may pay attention to the sources.list: only Natty genuine repo, desactivate everything else, then update

and force a fsck on next reboot:

sudo shutdown -r now

---

### Post by davelosm on 2011-08-29
OK, sources are done, but I don't know how to do the first bit you mentioned- the cache cleaning. What are the commands?

Thanks for the help

---

### Post by ajgreeny on 2011-08-29
> **davelosm said:**
> OK, sources are done, but I don't know how to do the first bit you mentioned- the cache cleaning. What are the commands?

Thanks for the help
> clean the cache: clean, autoclean, autoremove
That cleans the cache.

---

### Post by davelosm on 2011-08-29
OK I've done that now, didn't seem to make any difference.

Any other ideas?

Thanks

---

### Post by ajgreeny on 2011-08-29
Have you by any chance installed gnome3 or parts of it to have a look, as I note that there is a mention of gtk+3 as well as gtk+2.

I don't run 11.04, or not the ubuntu gnome version, so can not check that myself, and I don't know if gtk+3 is normal on a 11.04 installation.

---


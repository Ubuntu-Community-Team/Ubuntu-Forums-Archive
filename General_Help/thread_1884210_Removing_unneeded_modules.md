---
title: "Removing unneeded modules"
date: 2011-11-20
forum: General Help
---

### Post by Mahkoe on 2011-11-20
I am trying to fit a squashfs'd disk onto my hard drive, and I only need 45 more mb. Using the extremely handy disk usage analyzer, I was able to find out that the folder with kernel modules is 131 mb. I'm certain that if I was to delete the unneeded modules, I could at least get 30 mb, if not more. I could lsmod and then delete all the modules that aren't listed, but that's sloppy and seems like it would cause problems later. Any ideas?

I am using Ubuntu 10.10 64-bit

P.S. I have squashfs'd and loop mounted some of the larger folders with mhddfs (you should see my fstab), and I have deleted unneeded themes, removed all those crappy gnome games I got tired of, deleted the desktop backgrounds I don't use, bleachbit'd, deleted old kernels, cleared the apt cache, uninstalled redundant libraries (that took forever), and deleted guis when there was a command I could run instead. This is pretty much the last thing I can do to save space.

---

### Post by Mahkoe on 2011-11-21
bump

---

### Post by hwttdz on 2011-11-22
That's where I'd start.  Be aware that '-' in .ko objects sometimes (always?) turns into '_' in loaded objects, that and not everything lives in /lib/modules (but I suppose you're leaving the other ones?). 

Sounds interesting, but why are you doing this?

---


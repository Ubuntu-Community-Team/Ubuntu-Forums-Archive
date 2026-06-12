---
title: "Hotplug subsystem fails"
date: 2006-02-02
forum: General Help
---

### Post by ked on 2006-02-02
Hi All!

I'll try posting once more before I give up and reinstall Ubuntu (should really not be necessary :evil: )

Somehow hotplug does not work anymore (hangs on boot) and I've tried to locate the problem for 16 hours now... (and it's not the 'snd-hda-intel' kernel module. )

Is there any way to 'clean up' this mess?  I've got no wireless, sound or dvd/cd...

Again: PLEASE...anything is welcome....

Desperat...

---

### Post by dcstar on 2006-02-02
[QUOTE=ked]Hi All!

I'll try posting once more before I give up and reinstall Ubuntu (should really not be necessary :evil: )

Somehow hotplug does not work anymore (hangs on boot) and I've tried to locate the problem for 16 hours now... (and it's not the 'snd-hda-intel' kernel module. )

Is there any way to 'clean up' this mess?  I've got no wireless, sound or dvd/cd...

Again: PLEASE...anything is welcome....

Desperat...[/QUOTE]
Edit /etc/default/rcS to have:

VERBOSE=yes

That will give you more details on boot up to try and identify the problem.

---


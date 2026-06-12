---
title: "i need libvlc2 but i cant install it"
date: 2012-03-30
forum: General Help
---

### Post by eival on 2012-03-30
The following packages have unmet dependencies:
kamoso: Depends: libvlc2 (>= 1.0.0~rc) but it is not going to be installed
E: Broken packages

---

### Post by Silent Warrior on 2012-03-30
There's a command line invocation that lets APT provide suggestions, but I don't remember exactly what it looks like. What I would recommend, however, is pulling up Synaptic and remove (consider right-clicking and opting for Complete removal) any VLC/VLC2 packages, Apply, then reinstall VLC. This should get you the newer packages.

This kind of thing happens every so often if you're using PPAs or unstable software. This method is safe, as long as it's not a system-critical package or a core component of a DE.

---

### Post by laserator on 2012-04-01
I have a similar problem. Silent Warrior, is the removal then re-installation of VLCs the best method?

---

### Post by Silent Warrior on 2012-04-01
I'm far too swedish to suggest it's the best method, but in my experience, it works. I remember having the same issue once, and that's how I resolved it.

---


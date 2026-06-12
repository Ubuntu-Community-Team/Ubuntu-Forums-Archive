---
title: "Pretty Boot Screen in VMWare/VirtualBox?"
date: 2011-03-15
forum: General Help
---

### Post by mishathegoat on 2011-03-15
Hey everyone,
I've searched Google a number of times and couldn't find the answer to this question.

When I install Ubuntu 10.10 (or any other version) onto my virtual machine in VMWare, I don't see the pretty boot screen that appears on every other physical computer I boot Ubuntu off of. VMWare Fusion and VirtualBox both have a sort-of ugly text base boot which I really dislike (unless I'm trying to troubleshoot a boot problem). Any ideas how to get the pretty graphics and not the text-based 8bit-looking ugliness? Specifically, Plymouth's boot "graphics" in the virtual machine are downscaled... by a lot.

Any help is appreciated,
Thank you

---

### Post by LowSky on 2011-03-15
Nope its all plymouth's fault... You only get the nice graphics if it reconized the opensource driver. if not.. text based is all you see.
If you have an nvidia prorietary driver you get the same error. I've lived with this crap for a while now.

Sorry not much can be done as far as I know.

---

### Post by mishathegoat on 2011-03-15
Aw man that sucks... Well thanks for the response.

[EDIT]
At this point.. I'd like to replace plymouth with usplash (googling)

[Edit 2]
Which btw isn't possible.. for anyone who googled and found this..

---


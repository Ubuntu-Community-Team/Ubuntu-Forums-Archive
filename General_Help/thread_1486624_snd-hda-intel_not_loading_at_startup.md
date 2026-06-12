---
title: "snd-hda-intel not loading at startup"
date: 2010-05-18
forum: General Help
---

### Post by snowball.one on 2010-05-18
I posted this as a bug: [https://bugs.launchpad.net/bugs/580706](https://bugs.launchpad.net/bugs/580706)

On  Ubuntu Lucid Lynx, 64-bit, 2.6.32-22-generic kernel
When I log into the system, the speaker icon in the upper bar is black (just an outline) suggesting there is no sound output available. After further inspection I found that the snd-hda-intel kernel module isn't getting loaded.

I have to load the module myself (using 'modprobe snd-hda-intel')  every time I turn on the computer.


Anyone know what might be the issue?

---

### Post by snowball.one on 2010-05-19
Am I allowed to bump topics?

---

### Post by snowball.one on 2010-05-30
I just added snd-hda-intel into /etc/modules. I don't think it to be a proper fix, since it used to load the module automatically. Also, shouldn't my hardware be auto-detected and modules loaded appropriately?

---


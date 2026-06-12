---
title: "boot/shutdown dianosis"
date: 2010-09-04
forum: General Help
---

### Post by NiGhtMarEs0nWax on 2010-09-04
Hi, i am having some small issues with shutting down lucid, it seems to hand, unfortunately i cannot see what is causing this issue, is there anyway to check?

personally i thought it would be written to the console, ie tty1 etc, but it doesn't seem to show on any of them.. which is  weird. is there a way to turn off the lucid splash at boot and shutdown? it is rather ugly anyway.

---

### Post by Elfy on 2010-09-04
remove quiet and splash from the 

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" line

```
gksudo gedit /etc/default/grub
```

---

### Post by NiGhtMarEs0nWax on 2010-09-04
thanks man, i thought it might be something to do with the grub config, but unfortunately, i removed what you specified and nothing has changed.

i am using lucid and the install was a minimal install, using the minimal install iso. i don't know if that makes a difference, just thought i'd mention it.

---

### Post by Elfy on 2010-09-04
possibly because I forgot to tell you to run 

```
sudo update-grub
```

which should be done after any changes to grub.

---

### Post by NiGhtMarEs0nWax on 2010-09-04
Thanks man, yes that was perfect.

---


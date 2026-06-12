---
title: "nosplash disabled in grub2?"
date: 2010-05-19
forum: General Help
---

### Post by JohnnyC35 on 2010-05-19
hey, sorry if this is somewhere else but I haven't found it. I have found posts on changing the boot splash theme but not for disabling it. Previous grub you could disable the splash with 'nosplash' but with grub2 the splash screen still loads with Ubuntu and .... cycling.
in /etc/default I have this line
GRUB_CMDLINE_LINUX_DEFAULT="quiet nosplash noresume"
which should bypass looking for resume information and not show the splash screen. I know. I'm silly and actually want to see what's loading when it boots.

Any help would be appreciated :)

---

### Post by jbrown96 on 2010-05-19
Just uninstall all the plymouth packages, then update grub with ```
sudo update-grub
```

---

### Post by JohnnyC35 on 2010-05-19
hey thanks
... odd
I tried uninstalling 'plymouth' and it wanted to uninstall practically everything in my system. So I have instead uninstalled everything plymouth except for 'plymouth' 'libplymouth2'

will see if this works in 15 min, just waiting for some files to finish copying

---

### Post by JohnnyC35 on 2010-05-19
sweet!
it worked. and at least appeared to load a bit faster :P lol

---

### Post by Spr0k3t on 2010-05-19
> **JohnnyC35 said:**
> hey thanks
... odd
I tried uninstalling 'plymouth' and it wanted to uninstall practically everything in my system. So I have instead uninstalled everything plymouth except for 'plymouth' 'libplymouth2'

will see if this works in 15 min, just waiting for some files to finish copying

You can't uninstall plymouth itself.

> **philinux said:**
> Plymouth now has a hard dependency on mountall thus trying to remove Plymouth would remove half the OS. The advice is, if you don't want a graphical boot then uninstall any plymouth themes.

---


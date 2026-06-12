---
title: "Default volume levels on startup"
date: 2006-06-26
forum: General Help
---

### Post by Minn3h on 2006-06-26
Whenever I boot into Ubuntu, sound is always muted.  In the volume control both master and PCM are by default muted and at 0%.  It's a little thing, but I wish I didn't have to fix this every time I reboot.

---

### Post by vigleik on 2006-06-26
Strange. My volume never mutes, unless I do it myself of course. I think it comes back as the same as when I turned off my computer the last time. I guess I don't have an idea solution for you, but you could specify the volume in a little script you run when you log in. For kde you would put the script in $HOME/.kde/Autostart/, I'm not sure where you put it in gnome.

The script could say something like this: (after you install aumix)
#!/bin/bash
aumix -v 80 #main volume
aumix -w 80 #pcm

You might want to adjust it a little bit, but something like this should work, after you figure out where to put it.

Maybe someone else has a better solution.

Vigleik

---


---
title: "Emac fonts are not working after upgrade to 12.04 LTS"
date: 2012-04-27
forum: General Help
---

### Post by evoweiss on 2012-04-27
Hi all,

I think this is my first posting here, though it may not be.

Anyway, I've been able to resolve most problems via googling and what I know, but have come upon one at last that leaves me stumped. I've recently upgraded to Ubuntu 12.04 LTS. After doing so, my fonts in emacs, which I set to DejaVu Sans Mono 11 in the .Xresources file is no longer coming up. Moreover, I am unable to get any other font to work, either. Instead, all I get is the very ugly default font.

Prior to the upgrade, I had put the font definition in .Xresources and used xrdb --merge .Xresources to get it to work. However, the same trick is not working anymore. Neither is restarting Xorg.

Any help would be appreciated.

Best,

Alex

---

### Post by akk on 2012-04-27
I hit that problem too. It turned out to be that they've changed the emacs class name. I used to have lines like:

Emacs.font: DejaVu Sans Mono-9

That syntax has worked for a long time. But running xprop on the emacs window shows that the class name is now Emacs23 instead of Emacs. So I had to edit all my Emacs resources so they looked more like:

Emacs23.font: DejaVu Sans Mono-9

If they ever upgrade to emacs24 I guess we get to edit them all again. What was wrong with a class name of Emacs?

---


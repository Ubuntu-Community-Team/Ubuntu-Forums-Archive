---
title: "GoogleEarth in Kubuntu"
date: 2011-05-15
forum: General Help
---

### Post by scweston on 2011-05-15
Hi all,

I've just recently installed Kubuntu 11.04 and GoogleEarth. Unfortunately GoogleEarth looks really messed up with all the writing looking stretched (see attched picture). I've looked on this forum and generally on the web looking for how to fix it and although I do find things about fonts looking messed up, I can't seem to find the resolution to the problem.

Can I also add that I'm new to the KDE desktop. I've always been a bit of a Gnome fan, but not liking Unity or the Gnome Shell I thought I'd give KDE a try.

All help is appreciated.
Regards,
Stephen

---

### Post by Fxy on 2011-05-15
> **scweston said:**
> Hi all,

I've just recently installed Kubuntu 11.04 and GoogleEarth. Unfortunately GoogleEarth looks really messed up with all the writing looking stretched (see attched picture). I've looked on this forum and generally on the web looking for how to fix it and although I do find things about fonts looking messed up, I can't seem to find the resolution to the problem.

Can I also add that I'm new to the KDE desktop. I've always been a bit of a Gnome fan, but not liking Unity or the Gnome Shell I thought I'd give KDE a try.

All help is appreciated.
Regards,
Stephen

Dont really know if this is of any help...  ...But from your screenshot it looks like earth has somehow switched from using it's original font

Maybe you could try doing a reinstall of the program & see if that helps :?

---

### Post by oldos2er on 2011-05-15
You need ttf-mscorefonts-installer ```
sudo apt-get install ttf-mscorefonts-installer
```

---

### Post by scweston on 2011-05-16
Thanks oldos2er,

What you suggested worked, although only after completely restarting my computer (logging out and back in again wasn't enough either).

Although would still say it doesn't look the best i've seen google earth look.

Stephen

---


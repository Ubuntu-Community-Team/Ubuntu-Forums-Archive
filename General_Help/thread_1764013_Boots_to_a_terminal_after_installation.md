---
title: "Boots to a terminal after installation"
date: 2011-05-21
forum: General Help
---

### Post by Supergibbon on 2011-05-21
I've already posted this, but nobody seems to have any answer yet so I'm reposting in a different forum.
After installing 10.10 on my old desktop my monitor came up with the error 'Out of Range'.  I trawled the forums and learnt that this was a resolution thing that could be solved by adding 'nomodeset' to the grub menu, so I did this and reinstalled successfully, but now on booting it asks for my login and password and takes me to a terminal rather than the ubuntu I know from my laptop.  Any ideas?

---

### Post by sdowney717 on 2011-05-21
[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

try these ideas

---

### Post by Supergibbon on 2011-05-23
I'm new to this so may just be rubbish at spotting what part to use, but I had a go at installing xrandr and then running it and just got 'Can't open display' when trying to looking at my possible screen resolutions.  My monitor doesn't actually come up with 'Out of range' after I went into 'nomodeset', but as it now just goes into a terminal I've no idea if the resolution is still the problem.

(If it's any help I did lspci and figure the monitor line must be one that says:
01:00.0 VGA compatible controller: nVidia Corporation NV11DDR [GeForce2 MX200 rev b2) - though it does disappear off the side of the screen after the second 0 on MX200, so may carry on to say more).

---

### Post by Supergibbon on 2011-06-06
Got there in the end by loading crunchbang ubuntu and then nomodeset.  Suits me in the end as it's only an old 20gb hard drive and crunchbang's small : )

---


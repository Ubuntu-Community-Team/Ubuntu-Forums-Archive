---
title: "Problems with FLASH 64-bit, clicking doesnt always work"
date: 2009-10-17
forum: General Help
---

### Post by Theory5 on 2009-10-17
hey, I have trouble with my flash. I'm running Ubuntu 64-bit 9.10 and this is the first time flash has worked correctly so I can actually watch hulu. Before 9.10 flash ran to slowly to watch. But now I cant click buttons a lot of the time. This is a minor problem because I can pause the movie with the space bar, which works correctly. Anyone know how to fix this?

---

### Post by Johnny B on 2009-10-17
try this tutorial/script:
[http://ubuntuforums.org/showthread.php?t=1233235]("http://ubuntuforums.org/showthread.php?t=1233235")

---

### Post by dardack on 2009-10-30
> **Theory5 said:**
> hey, I have trouble with my flash. I'm running Ubuntu 64-bit 9.10 and this is the first time flash has worked correctly so I can actually watch hulu. Before 9.10 flash ran to slowly to watch. But now I cant click buttons a lot of the time. This is a minor problem because I can pause the movie with the space bar, which works correctly. Anyone know how to fix this?

You ever get this fixed?  I get full screen clicking fine in youtube, but once i go to Hulu.com, no clicking works, so no Fullscreen.

---

### Post by Monotoko on 2009-10-30
I got it fixed, follow this on the 64bit section: [http://ubuntuforums.org/showthread.php?t=1259102](http://ubuntuforums.org/showthread.php?t=1259102)

Remove all other flash's you might have first using apt-get remove

---

### Post by dardack on 2009-10-30
> **Monotoko said:**
> I got it fixed, follow this on the 64bit section: [http://ubuntuforums.org/showthread.php?t=1259102](http://ubuntuforums.org/showthread.php?t=1259102)

Remove all other flash's you might have first using apt-get remove

So you can click on the pause/sound/fullscreen/HD/Embed/popout inside Hulu?

Hulu is the only site that doesn't work for me 100%.  It plays videos, and i can play/pause with space, but "f" doesn't work for Fullscreen, and i can't click on anything.  (not true, sometimes popout works, maybe 30%, if i continuously click it eventually works, and the sound, but i can never click HD/Fullscreen, ever, or the pause button).

EDIT: Forgot, the upgrade messed up my OS, so i had to do fresh install so forgot that the flash in repo's isn't the 64bit alpha, will install the 64bit alpha when I get home to see if this resolves the issue.

EDIT2: Small work arond for the clicking, click outside the flash, hold mouse button, move cursor over the button you want to click in flash, release and click button quickly, and now clicking works.

---

### Post by niekko on 2009-10-31
This bug might be related: [https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/410407](https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/410407).

---

### Post by kalmos on 2009-12-29
> **dardack said:**
> EDIT2: Small work arond for the clicking, click outside the flash, hold mouse button, move cursor over the button you want to click in flash, release and click button quickly, and now clicking works.

Thanks for this tip! It works for me, now I can fullscreen and all the rest. :)

I followed the instructions on this page in an attempt to fix the Hulu issues:
[**Adobe Flash install information for AMD64 (December 2009 update)**]("http://ubuntuforums.org/showthread.php?t=1358591")

---


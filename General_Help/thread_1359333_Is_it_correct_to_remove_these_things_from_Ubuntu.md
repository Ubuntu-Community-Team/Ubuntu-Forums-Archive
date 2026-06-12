---
title: "Is it correct to remove these things from Ubuntu?"
date: 2009-12-19
forum: General Help
---

### Post by pluto4ps on 2009-12-19
Hi,
I thought to see what the "Computer Janitor" program does and it says I can remove these files. But I am not sure because I am new to Ubuntu and really afraid to do...

Please help me out....

---

### Post by jflaker on 2009-12-19
Try this:
open a terminal session and purge old/no longer required dependencies...

sudo apt-get purge&&sudo apt-get autoremove

after you run this, refresh computer janitor and you should see less.

As for unsupported stuff, unless you are using it, you can likely remove it.

---

### Post by howefield on 2009-12-19
Use a bit of common sense, eg, if you still use Virtualbox, don't uninstall it.

Make a note of what you are removing, in case you have unintended consequences.

I just fired it up after reading your post, for me, it only wants to remove programs which were installed outside of the repository, there is nothing in the list I'd be happy to lose, you need to use your judgement and be careful.

To be honest, unless you are strapped for space, why remove anything on your list ?

---

### Post by pluto4ps on 2009-12-19
Naturally I came from Windows, and worried like registry, temp files, etc etc...I felt like may be Ubuntu will slow down, then I thought Oh!!!! its Ubuntu, but still that Windows GHOST don't go away suddenly....LOL...

---

### Post by pluto4ps on 2009-12-19
How to know if it shows like in First Screenshot, I don't know what that all means like lib, libsvga, mplayer-nogui etc, it bit difficult, right?

---

### Post by oldos2er on 2009-12-19
> **pluto4ps said:**
> Naturally I came from Windows, and worried like registry, temp files, etc etc...I felt like may be Ubuntu will slow down, then I thought Oh!!!! its Ubuntu, but still that Windows GHOST don't go away suddenly....LOL...

What registry? /tmp is cleared on reboot.

---


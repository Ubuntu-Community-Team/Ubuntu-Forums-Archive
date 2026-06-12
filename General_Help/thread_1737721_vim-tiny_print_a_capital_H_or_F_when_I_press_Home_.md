---
title: "vim-tiny print a capital H or F when I press Home or End button"
date: 2011-04-23
forum: General Help
---

### Post by bingel on 2011-04-23
Some days ago I upgraded libc6 to a newer version (from version provided by lucid to version provided by natty).
Since with new version I had some problems, then I downgraded libc6 to original version.

But after upgrade/downgrade, vim-tiny doesn't work as before: either in "insert mode" than in "command mode", when I press "HOME" or "END" keys, just a capital "H" or a "F" is printed.

Situation doesn't change neither if I set "nocompatible" mode or "esckeys" mode.

I think this problem is related to updating of the locales that occurred during the upgrade of libc6 but also reconfiguring everything, vim-tiny does not work correctly and however, this is only my guess.

I must point out, further, that this only happens from the terminal window. From the virtual console everything is ok.
 My desktop environment is lxde (Lubuntu) and terminal is lxterminal.

Any idea?

---


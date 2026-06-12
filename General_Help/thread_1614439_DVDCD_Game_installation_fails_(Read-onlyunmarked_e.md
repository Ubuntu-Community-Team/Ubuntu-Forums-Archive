---
title: "DVD/CD Game installation fails (Read-only/unmarked executable)"
date: 2010-11-05
forum: General Help
---

### Post by gngf123 on 2010-11-05
So I am trying to install a game to use with WINE from a CD I have lying around. However, the game installer isn't a marked executable file, and I am unable to make it one because I only have read access to the disk.

(Using Ubuntu 10.10)

Is there anything I can do here?

EDIT:

Nevermind, Just like me, I try for hours and solve it the moment I tell someone about it.

running wine setup.exe from the terminal seems to have done the trick.

---

### Post by mc4man on 2010-11-05
see here - same basic idea - use wine instead of "Wine Windows Program Loader'
[http://ubuntuforums.org/showthread.php?p=10075810#post10075810](http://ubuntuforums.org/showthread.php?p=10075810#post10075810)

Post 2 under 'thirdly'
or Post 3 - 

Another option is to create a typical mountpoint and fstab entry as was done pre-lucid.
I do that here - the mount options will override this nonsense

---


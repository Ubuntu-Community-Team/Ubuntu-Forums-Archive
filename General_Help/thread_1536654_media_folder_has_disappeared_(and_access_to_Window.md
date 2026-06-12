---
title: "/media folder has disappeared (and access to Windows partition)"
date: 2010-07-22
forum: General Help
---

### Post by bluelamp999 on 2010-07-22
Hi all,

I'm running 10.04 on a system with a Windows XP partition (dual boot.)

Usually, when I start a Ubuntu session my Windows partition (called 34 GB Filesystem) is available to browse in Nautilus and from a drive icon on the desktop.

However, this evening when I logged in the desktop icon is no longer there and though '34 GB Filesystem' is still visible in Nautilus when I try to browse/mount I get "Unable to mount 34 GB Filesystem - Error creating moint point: No such file or directory".

Has anyone any idea what's happened here?

I did fire up Windows last night (first time in ages!) and had to download the usual tranche of updates and 'security' updates - could this have broken something?

I can still launch Windows from Grub and all seems normal but it's weird that I can't access the partition any more - I access it frequently to save stuff there.

Also, I now have no /media folder. Are these facts related?

Any help gratefully received!

Thanks

---

### Post by bluelamp999 on 2010-07-22
OK.

The clue to solving this was in the title!

By creating a new /media folder everything is now back to normal.

I must somehow have deleted the /media folder - Duh!

You learn something new every day...

---


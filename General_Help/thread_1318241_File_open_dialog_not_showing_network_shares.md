---
title: "File open dialog not showing network shares"
date: 2009-11-07
forum: General Help
---

### Post by shineymart on 2009-11-07
In 9.10 if I connect to a network share using places->connect to server the share is not shown in all File Open dialogs.

I've seen discussion about this issue relating to OOo in 8.10 but in 9.10 it seems to work better... I can report the following:

1. Nautilus shows both the mounted share AND the bookmark
2. The mounted share appears as a link on my desktop
3. Gnome apps show both the mounted share AND the bookmark
4. OpenOffice shows only the mounted share
5. Firefox and other apps (pgAdmin 111 for example) don't show either the share or the bookmark

Obviously if I press ctrl-h while in the file open dialog for, say, Firefox the mounted shares show up under .gvfs

It seems therefore that non-gnome apps except OOo aren't showing network shares.

Anybody got any fixes for this? Asking civilian (ex windows) users to 'sometimes' press ctrl-h and navigate to hidden folders is not where I want to be. 

Thanks
Martyn

---

### Post by shineymart on 2009-11-15
Anybody able to help?

---

### Post by Dave-B on 2010-07-23
> **shineymart said:**
> In 9.10 if I connect to a network share using places->connect to server the share is not shown in all File Open dialogs.


Yeah, very annoying. Please mark [https://bugs.launchpad.net/ubuntu/+source/gtk+2.0/+bug/304345](https://bugs.launchpad.net/ubuntu/+source/gtk+2.0/+bug/304345) as affecting you, as that might help raise it's profile a little.

Cheers,
Dave.

---


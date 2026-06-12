---
title: "Karmic won't start after crash on bad shutdown"
date: 2009-12-07
forum: General Help
---

### Post by peutch on 2009-12-07
Hi everyone,

By mistake, I pulled out the plug while my Karmic was shutting down.

Now when I boot, everything seems to go fine at the beginning, I get the loadbar, but after that, when the "curtain" background is supposed to be replaced by my own desktop, with sidebars etc. my computer freezes... Ctrl Alt Del won't do anything (or any combination of keys) and the only thing left for me is a hard power off.

Any idea on a potential diagnostic? I don't even know where to start.

Thanks!

Patrick

---

### Post by peutch on 2009-12-07
PS: I forgot to mention:
- this happens after I've logged in normally using the login menu.
- it displays two messages. The first one is very quick and I can't read it properly but it says something the energy profile not being set, or something like this. The second one is "Ubuntu one: syncing your files".

Then it freezes. I don't think it's a pb with Ubuntu One because what started this whole thing is a (very) hard shutdown.

Thanks for any ideas that might help.
I've just done a fckdsk -f to check the files, but to no avail.

---

### Post by peutch on 2009-12-09
Up!

Any idea to get started on this?

---

### Post by bumanie on 2009-12-09
Boot a live cd and try this code in terminal > sudo e2fsck -C0 -p -f -v /dev/sdxxReplacing xx with your drive letter and number eg /dev/sdb2.

---

### Post by peutch on 2009-12-09
Thanks, sorry for the delay, this problem is imposing some logistic constraints, but I'll let you know how this goes as soon I can burn the image.

Patrick

---

### Post by peutch on 2009-12-12
Hi !

I tried what you told me, but it didn't mention any broken file, in either my /home partition or my / partition.

However, I have since then reinstalled Karmic after formatting the "/" and it still blocks at the same point, so something tells me it might be a problem with my personal config files somewhere. Probably something related to the desktop, I must assume, since it blocks at the point at which the desktop should be displayed. (On the other hand, it could be caused by any other background process happening at the same time...)

Thanks!

Patrick

---

### Post by peutch on 2009-12-12
I've solved my problem by looking at the syslog. There was a corruption of my gconf it seems. Delete the .gconf folder (my display preferences), has enabled me to get the system back!

Now I just need to re-customise my desktop (and reinstall all the applications I had needlessly removed by reinstalling Karmic). On the plus side, I now have a clean system!

Patrick

---


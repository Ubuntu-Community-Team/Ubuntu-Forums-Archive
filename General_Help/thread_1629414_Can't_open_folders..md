---
title: "Can't open folders."
date: 2010-11-23
forum: General Help
---

### Post by Jerfo on 2010-11-23
I begun with this problem earlier this morning, for some reason I can't open any folder located on the Sources (I'm unsure about the name, I'm translating from French, anyway, it's the one between Applications and System menu) menu, I just keep getting an error message that goes something like this:

'Impossible to open the place "whatever"

No application associated to handle this file.'

I haven't changed nor installed anything that could explain this behavior, I can open folders elsewhere without any problem (i.e. located in the desktop, if I manually open Nautilus or whichever other way.) 

So, any ideas?

---

### Post by dcstar on 2010-11-24
> **Jerfo said:**
> I begun with this problem earlier this morning, for some reason I can't open any folder located on the Sources (I'm unsure about the name, I'm translating from French, anyway, it's the one between Applications and System menu) menu, I just keep getting an error message that goes something like this:

'Impossible to open the place "whatever"

No application associated to handle this file.'

I haven't changed nor installed anything that could explain this behavior, I can open folders elsewhere without any problem (i.e. located in the desktop, if I manually open Nautilus or whichever other way.) 

So, any ideas?

It is the Places menu:

[http://ubuntuforums.org/showthread.php?t=1505483](http://ubuntuforums.org/showthread.php?t=1505483)

---

### Post by mc4man on 2010-11-24
In the future **(after** fixing this occurrence) - whenever using the 'other application' menu you'll need to uncheck the "Remember this application..." box or whatever you pick will become the new default.
(on 10.10 this mis-behavior affects both files and folders, not sure about files in 10.04

---

### Post by Jerfo on 2010-11-24
Thank you very much! For some reason the 

"inode/directory=nautilus-folder-handler.desktop;"

Appeared under "Removed Associations" in the mimeapps.list. No idea how this happened but I'm glad that annoying problem is gone.

---


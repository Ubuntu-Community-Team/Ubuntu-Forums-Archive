---
title: "Folder &quot;Modified Date&quot; problem"
date: 2011-12-04
forum: General Help
---

### Post by arst06d on 2011-12-04
Hi

I am using TVMobili to stream my music, and have noticed that the cataloguing of my music appears to stop at the lowest folder in the tree, checks the Modified date of that folder and, if no change, it ignores any changed files within the folder.
For example, I change the Artist tag on a mp3 file.  The file Modified date is changed but the folder Modified date is not.
If I duplicate a file within the folder, then delete it, then the folder Modified date is updated.

Is this a glitch in Ubuntu or is this how things are supposed to work?  Any workarounds or config settings I can change so that file changes will automatically modify the containing folder Modified property?

---

### Post by Musgrave on 2012-07-31
I had a similar problem. Only the immediate parent directory 'date modified' field was updated in Nautilus (Dolphin and 'ls -l' showed updated fields). 
Rsync was ignoring directories where files had been changed 2 levels down. I reconfigured the language setting in gnome-control-center and this 'fixed' it.

---


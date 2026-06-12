---
title: "Audacity and VST's - A Ubuntu problem..."
date: 2010-10-23
forum: General Help
---

### Post by icebeat on 2010-10-23
Ok here's the problem as I see it (and I'm fairly new to Ubuntu).  Why is it you download Audacity (and other awesome free audio programs) in synaptic package manager and they store all (with the exception of Linux Multi-Media Studio) in sub folders and plugin directories in different folders in the file system??  There are no administrative permissions there, which means you can't install plugins in Audacity because you can't copy or paste anything in the file system where it is stored.  How does anyone else using Audacity in Linux install plugins and VST's??

J

---

### Post by themusicalduck on 2010-10-23
To be able to write to parts of the filesystem where you don't have privileges, you need to run the file browser as root.

Press alt+f2 and type in ```
gksudo nautilus
``` then put in your password.

The plugins need to be saved in /usr/share/audacity/plug-ins.

I'm not sure about using VSTs. I think in general you can't because they are mostly made for Windows. You might be able to find out more about it with some googling. I think it might be possible using a VST host in Wine with Jack.

---


---
title: "Does uninstaling VirtualBox also delete WinXP installation?"
date: 2011-11-29
forum: General Help
---

### Post by Leo Reijnen on 2011-11-29
I have removed Sun VirtualBox from my Ubuntu 11.10 (oneiric) system. Does this mean that the Windows XP + programmes I installed earlier there are also gone? I don't mind, but I don't want to waste disc space and I don't know where to look for left-over folders and files, if any.
Any advice is highly appreciated.

---

### Post by mutley89 on 2011-11-29
By default they are stored in '~/VirtualBox VMs/'.  There is probably also some related data under ~/.VirtualBox

---

### Post by StevenStip on 2011-11-29
if you're concerned about diskspace you can always use command line df and df -H to see how much is in use and there is this disk usage monitor that shows you where your disk space is being used.

---

### Post by Leo Reijnen on 2011-11-30
Thanks. I found 5.6 Gb I could remove!

---


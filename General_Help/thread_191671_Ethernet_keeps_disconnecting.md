---
title: "Ethernet keeps disconnecting"
date: 2006-06-07
forum: General Help
---

### Post by subtex on 2006-06-07
When I boot up my laptop, the ethernet connection shows up dead.  If I unplug and replug the ethernet cable, internet will work fine for maybe 45 seconds or so, then disconnect itself again (red exclamation over the icon).

My laptop is an older Winbook X1.

I searched the forums a bit and found the command "lspci".  I ran that and found my ethernet is showing up as:

```
Davicom Semiconductor, Inc. 21x4x DEC-Tulip Compatible 10/100 Ethernet (rev 31)
```

I had no problems at all with Breezy on this laptop.

Any suggestions?  

My linux knowledge is fairly low, so any newb friendly help would be greatly appreciated.

---

### Post by tonyr on 2006-06-07
It's a common problem with that controller. Read [this]("http://www.ubuntuforums.org/showthread.php?t=186430") thread,
then post back here if you have questions.

---

### Post by subtex on 2006-06-07
That did it.  Works like a charm now.  Thanks for the help!

---


---
title: "Weird problem with my netbook"
date: 2012-09-04
forum: General Help
---

### Post by Derek10 on 2012-09-04
I have Xubuntu 12.0.4 32 bit on my Samsung N145P netbook with the brighness fix (samsung tools).

Since last bunch of updates, now sometimes freezes upon bootup, in a black screen without backlight, 

Once, after 1 minute in that state, the backlight came on, but black screen, and the caps lock LED started to flash fast and infinite, but the netbook was so hard locked I had to pull out the battery to reset it.

After this freeze, the next boot I get an error regarding brightness control before going to desktop despite it works fine and once besides the touchpad was frozen but keyboard worked.

Any help will be appreciated.

---

### Post by black veils on 2012-09-04
when you boot, hold the shift key, and you will eventually see the grub boot loader, with kernels listed etc. try the previous kernel version number from what is currently being used (latest is at the top). boot into that by pressing the enter key. keep using the system like that to see if the errors are gone. 

if the errors no longer occur in the previous kernel version, then you could install and use ```
startupmanager
``` to specify the default kernel.

or find a safe way to remove the new kernel, and lock the previous.

---

### Post by Derek10 on 2012-09-04
Many thanks. The kernel doesn't appear to be updated in the latest batch of updates where the problem has started a only appears one version. I can't know what's going on as Ubuntu always worked flawlessly here (Windows 8 is fine so I rule out any hardware problem)

---


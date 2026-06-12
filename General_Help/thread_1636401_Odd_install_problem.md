---
title: "Odd install problem"
date: 2010-12-03
forum: General Help
---

### Post by TNT1 on 2010-12-03
I recently made a remastersys .iso of my install of 10.04.1, so I could format and re-install my laptop. I tried to install the same on my wife's laptop this morning, and it goes fine till the select partition stage, where it shows nothing, and tells me that there is no partition, and I need to correct it using the partition editor, only problem, is that all the options except "back" are greyed out.

And it worked fine when I re-installed, as I formatted at that point. (oh, she is currently running 10.04.1)

---

### Post by sikander3786 on 2010-12-03
Go to Terminal and post the output of this one.

```
sudo fdisk -l
```

And make sure under Bios, hdd is set to ahci or compatible mode.

---


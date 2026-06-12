---
title: "Live CD 10.10 wirless"
date: 2010-12-28
forum: General Help
---

### Post by SG12010 on 2010-12-28
With Ubuntu 10.10 live cd Lan and Wireless work fine but when installed on Hardrive Lan and wireless fail to work.

---

### Post by amsterdamharu on 2010-12-28
Could you tell me the output of the following commands?

```
sudo lshw -C network
```

```
lsmod
```

```
iwconfig
```

To execute the commands you can press alt + F1, type gnome-terminal and click run. Then copy one command and paste it in the terminal (black screen that showed up after you clicked run). Use the mouse to paste commands in the terminal.
Then you can select all the text in the terminal, right click and select copy. When pasting it here please wrap it in &#91;code] &#91;/code] tags.

---

### Post by spiky001 on 2010-12-28
Try adding the cd to software sources, Then use update manager with cd in drive, see if that loads the drivers /System/Administration/Hardware Drivers

---


---
title: "Grub problem"
date: 2011-02-16
forum: General Help
---

### Post by clint8679 on 2011-02-16
I am having a re-occuring problem with Grub. The problem seems to occur about once every 15 or so times that I start up.

Basically, it gets past the Samsung branded screen but before it goes to the Grub screen, the computer will restart - it just continually gets to this point and restarts until I shut down with the power button.

The problem is easily fixed by re-installing Grub using an ubuntu CD.  Things will then run fine for about a week and the same problem will occur.

Any thoughts would be welcome

---

### Post by Rubi1200 on 2011-02-16
To help us get a better look at what is happening, please do the following:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---


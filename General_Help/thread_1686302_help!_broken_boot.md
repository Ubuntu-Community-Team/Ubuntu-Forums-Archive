---
title: "help! broken boot"
date: 2011-02-12
forum: General Help
---

### Post by gandaran on 2011-02-12
hi,
I cant boot ubuntu, all I get is init file not found and initranfs prompt, I type help and get a list of commands and typing any command only shows list of errors, this is the second time this happens on the desktop, ubuntu is the only OS on desktop and I,m fed up with ubuntu 10.10 but would like to fix it or I will have to install windows until the next ubuntu release comes out.
thanks

---

### Post by gandaran on 2011-02-12
help..............

---

### Post by Rubi1200 on 2011-02-12
Sorry to hear you are having problems.

Please do the following:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---


---
title: "Mounting Failure"
date: 2011-03-22
forum: General Help
---

### Post by carolina on 2011-03-22
Using Ubuntu 10.4 on pc with dual boot Windows XP . Can't get to Ubuntu to boot after restart.

mounting /sys on/root/sys failed
mounting /dev on/root/dev failed
mounting/ proc on/root/proc failed

any help appreciated...

---

### Post by Rubi1200 on 2011-03-22
Hi,

please do the following:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the _entire_ contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---


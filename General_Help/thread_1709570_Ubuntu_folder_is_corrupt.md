---
title: "Ubuntu folder is corrupt"
date: 2011-03-18
forum: General Help
---

### Post by mahnerak on 2011-03-18
Yesterday I turned on my computer in Ubuntu OS, but loaded GRUB. I tried to open D:\Ubuntu folder from Windows XP, but appears alarm "File or folder is corrupt or unreadable". I installed Ubuntu from WUBI to partition D:\ without formating 5 days ago. I can't uninstall Ubuntu. How can I repair my system?

---

### Post by Rubi1200 on 2011-03-18
Hi and welcome to the forums :-)

Please do the following so we can see what is going on:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the _entire_ contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---


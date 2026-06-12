---
title: "Ubuntu will not load"
date: 2011-03-01
forum: General Help
---

### Post by Mastrius0713 on 2011-03-01
I need help, I don't know what happened but I had loaded the latest security updates on Ubuntu 8.04, as the little notifier said, and later when I rebooted the comp, the startup process stopped at a command prompt which says:

> 
BusyBox v1.1.3 (debian 1:1.1.3-5ubuntu12) Built-in shell (ash)
Enter 'Help' for a list of built in commands.

(initramfs)


How do I get back into Gnome so I can rescue my bookmarks and important documents?

---

### Post by Rubi1200 on 2011-03-02
Hi,

the first thing to try is boot the computer with a LiveCD and copy off all your important data to an external medium.

Then, do the following:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---


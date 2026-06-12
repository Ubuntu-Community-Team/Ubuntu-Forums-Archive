---
title: "wubi/xubuntu boot failure"
date: 2011-04-23
forum: General Help
---

### Post by Rhodium on 2011-04-23
Hi im joey i a total noob to linux based OS and i tried to install xubuntu on my desktop using wubi..it instaled and everything when i tired to boot xubuntu it said
```
Gave up waiting for root device. Common Problems:
 -Check rootdelay=(did the system wait long enough?)
 -Check root=(did the system wait for the right device?)
-Missing Modules (cat /proc/modules; ls /dev
ALERT! /dev/sdb3 does not exist. Dropping to a shell!

BusyBox.........
```

okay now when i try to boot window$ vi$ta and re Install WUBI window$ cant boot either
what should i do?

---

### Post by Rubi1200 on 2011-04-24
Hi and welcome to the forums :-)

We need to know what is going on with the system.

To that end, please do the following:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---


---
title: "Dual Boot Ubuntu/windows Grub problem. Cant see windows."
date: 2010-10-26
forum: General Help
---

### Post by awd01 on 2010-10-26
Greetings GUYS, I know that there are thousands of topics about these problems but i cant find a solution. my problem is the following. 
I had ubuntu and i decided to install windows after some problems i made a partition and I installed windows. After that windows were running normally but i couldnt see and run Ubuntu so I did this ```
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
``` I run an ubuntu live cd I installed grub and ubuntu are running perfectly but now I cant see windows and also I cant see the grub menu.

some info:
-Ubuntu 10.04
-Windows 7
-Grub 2

---

### Post by oldfred on 2010-10-26
If grub2 only sees one system it skips the menu. You should be able to hold down the shift key from BIOS boot until menu appears to get menu.

To get grub to update menu and search for the windows install.

```
sudo update-grub
```

---

### Post by awd01 on 2010-10-27
> **oldfred said:**
> If grub2 only sees one system it skips the menu. You should be able to hold down the shift key from BIOS boot until menu appears to get menu.

To get grub to update menu and search for the windows install.

```
sudo update-grub
```


My friend I did it and everything is working perfect! Thank you very much!!!

                                             :):guitar::)

---


---
title: "change from wubi to complete installation"
date: 2010-10-26
forum: General Help
---

### Post by boghadab on 2010-10-26
hi, i am trying to move my installation from my wubi drive to another drive, i use LVPM, but the listed partitions in LVPM, doesnt mention which partition is which , the available space in each partition is not listed, there are 5 partition in the MOVE section in LVPM, any clues of how to find out which is which, please urgent help, performance is not perfect with the WUBI installation. appreciate any help.

---

### Post by bcbc on 2010-10-26
lvpm does not work properly with current versions of ubuntu.

If you've already installed it, it probably uninstalled grub-pc and replaced it with grub. So you should reinstall grub-pc (taking care to NOT install it to any devices if it prompts you e.g. /dev/sda, /dev/sda1, /dev/loop0).

then use this: [http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

You need to know which partition you will be moving it to with the above guide. If you use the script it will check the space, but it doesn't prompt you the way lvpm does.

---


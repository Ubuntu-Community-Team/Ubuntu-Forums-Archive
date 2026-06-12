---
title: "udev rule for sdcard"
date: 2011-02-11
forum: General Help
---

### Post by Nathanael Culver on 2011-02-11
I'm trying to write a udev rule for my sdcards, following the tutorial at [http://ubuntuforums.org/showthread.php?t=1290438](http://ubuntuforums.org/showthread.php?t=1290438). I'm running into several problems.

I want to distinguish a specific sdcard and run a script accordingly: for my backup sdcard a backup script; for my camera's sdcard a script to copy pictures off. And I want it to work regardless of whether I plug the card into the internal slot or via a USB adapter.

First, I'm having difficulty identifying specific sdcards. Been looking at output from _udevadm info -a -p  $(udevadm info -q path -n /dev/sdb1)_ and I can't find anything that helps me distinguish between the two cards. According to the udev manpage, TEST{octal mode mask} can be used to look for a file, so I'm trying to use that.

Here's what I've done:

1. Created /etc/udev/rules.d/91-local.rules with:

```
TEST="sdcard1" RUN+="/home/nathanael/USB"
```

2. Created a file on the sdcard called "sdcard1".

3. Created and chmod +x'ed /home/nathanael/USB:

```
#!/bin/bash
echo 'Hello World!' >>"/home/nathanael/udev.out"
exit
```

The script works when run manually, but it doesn't fire when I plug in the card.

Help.

--Nathanel

---

### Post by Nathanael Culver on 2011-02-11
Bump.
Bump.

---

### Post by Nathanael Culver on 2011-02-11
Bump

---


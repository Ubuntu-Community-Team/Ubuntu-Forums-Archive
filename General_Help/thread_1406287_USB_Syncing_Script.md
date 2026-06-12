---
title: "USB Syncing Script?"
date: 2010-02-13
forum: General Help
---

### Post by ben-ess08 on 2010-02-13
I need to create a script that will select all files of a certain type (.mp3) and make it copy it to a directory in one big batch, so I will be able to sync it with the USB drive, any help on what commands I should use to make it select all the .mp3 files ? Thanks :D

---

### Post by ironclaw on 2010-02-13
You can use regular expressions with cp:
```
cp ./*.mp3 <dest>
```
This will copy all files ending with '.mp3' in the current directory to <dest>.

You also mentioned syncing with a USB drive - the 'rsync' command is quite useful in syncing files between 2 devices.

---


---
title: "Space disappears"
date: 2009-11-09
forum: General Help
---

### Post by ipburbank on 2009-11-09
Hello, I just re-installed, and un-packed the tar I made of my files. It appears that the amount of space ubuntu says my home folder takes up, and how much space it uses on the drive are quite different. Could this be the hidden backup files? It is around twice the amount of size ubuntu says the folder is, that is no longer avalable on the hd. Said in a way that makes sense, I clicked 'properties' for my home folder, and it says it contains around 300 GB. When I created a .tar it was 200GB, and when I un-compressed it it was 300 again. That is all good except I uncompressed it on a drive that had 800GB left on it - there was only 200 left after I un-compressed it.

If this is from the backup files, what is a command I can use to delete the backup files where:
[LIST]
[*]the original file exists
[*]the original file hasn't been modified in over 2 months
[/LIST]

~Thanks in advance, Istvan.

---

### Post by blueridgedog on 2009-11-09
You can track down the space waster by going to the root of the drive (the mount point) and issuing:

sudo du --max-depth=1 | sort -g

This will shows directory sizes small to large.  It may help you find the cause of the size issue.

---


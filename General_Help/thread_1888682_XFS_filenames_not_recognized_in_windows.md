---
title: "XFS filenames not recognized in windows"
date: 2011-11-29
forum: General Help
---

### Post by Kissell on 2011-11-29
I have a fileserver running an XFS volume that is shared via samba.

XFS lets me do things like name filenames with characters that windows thinks are invalid.  For instance XFS thinks there is no problem to name a file: "myworld?.txt" but then when I try to view this from a windows PC the filename is random garbage characters.

Is there an easy way to modify the following mount code to force Ubuntu to only allow characters windows likes?  

> 
sudo mount -t xfs /dev/sdb1 /mnt/data


---


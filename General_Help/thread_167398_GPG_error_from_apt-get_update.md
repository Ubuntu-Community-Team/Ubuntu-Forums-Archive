---
title: "GPG error from apt-get update"
date: 2006-04-28
forum: General Help
---

### Post by hell0un1verse on 2006-04-28
Hi there, I can't remember what I could have done wrong, but recently I have been getting this **message** at the tail of the **command**'s console output:

**Message**: Fetched 192B in 1s (120B/s)
Reading package lists... Done
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: You may want to run apt-get update to correct these problems


**Command**: sudo apt-get update

Anybody knows why that is? Your reply will be truly appreciated.

---

### Post by hell0un1verse on 2006-04-28
Any clue?

---

### Post by taniwhaiti on 2006-04-28
i'm getting the same errors from both home and work machines.

Looks like something's gone wrong with ubuntu deb signings.. have they changed key?  should we trust the new one?

---


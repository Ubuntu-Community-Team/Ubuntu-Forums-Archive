---
title: "Is there a problem accessing a large directory on a FreeNAS server from Ubuntu Natty?"
date: 2012-04-27
forum: General Help
---

### Post by Bullwinkle_Moose on 2012-04-27
We're seeing an issue where it appears that if there are somewhere around 500 files in a FreeNAS directory (on another server on the local network), our Ubuntu Natty-based media center simply refuses to read the directory until one or two of the files are moved out of the directory (weirdly, in at least one case it would also read the directory if the most recently added file was renamed to 1.m4v).  This only appears to be a problem on the computer running Ubuntu Natty; we do not see this issue on any other computer on the network that accesses the same FreeNAS server.  This happens whether we are accessing the directory from inside XBMC or from Ubuntu Natty's native file browser.  We are wondering if anyone else has run into this.

We don't understand this behavior, particularly when other (non-Ubuntu) computers have no issues at all accessing this directory.  If we break up the files into smaller directories there is no issue but we really don't want to do that, and besides one would think that Ubuntu should not have an issue with even thousands of files in a directory, let alone a few hundred! If ANYONE can explain why this happens and/or offer a solution to this issue, it would be very much appreciated!

---

### Post by Bullwinkle_Moose on 2012-04-27
I edited the above to clarify that this happens in both Ububtu's native file browser and in software (such as XBMC) running under Ubuntu, but not on any other computer we've tried it from on the local network.  I hope someone can shed some light on this because it's driving us crazy.

---

### Post by Bullwinkle_Moose on 2012-04-29
It turns out this bug in Ubuntu has been around for a while - see [http://ubuntuforums.org/showthread.php?t=1359375](http://ubuntuforums.org/showthread.php?t=1359375)

---


---
title: "Problem with USB 32 GB Flash drive"
date: 2010-01-31
forum: General Help
---

### Post by keevill on 2010-01-31
Using a 32 GB USB Flash Drive -PC's running Ubuntu 9.10 - 
When the Drive is plugged in the following occurs.
Machine A can see and has read/write capability ( normal behaviour )
Machine B can see the media but can see no files on it created by Machine A 
However Machine B can create new file/folder- This file cannot be seen by Machine A.
When I plug the thumb drive back into Machine B - no files ( including the one created by itself ) can be seen.
Win machines have no problem.
I've tried Gpart to format to Ext2 / 3 . 
Its currently formatted to Fat32

---

### Post by kronomia on 2010-01-31
Try to format both of them to ext3 - to the fact that fat32 should work fine. Check also the permissions and settings for users and groups in your system. One more thing you can try is to connect them after booting from a live Linux CD. By the way, have you tried using them through other machines? or other Operating Systems apart from windows?

---


---
title: "Weird permissions issue when saving files"
date: 2012-07-20
forum: General Help
---

### Post by GuiGuy on 2012-07-20
Hi,
From Nautilus I can access shares on a NAS device mounted on my local PC. I can add/ edit and delete files using Nautilus, a shell etc.. I suspect I have mounted the shares correctly. 

```
drwxrwxrwx  2 1001 1001 0 2012-07-17 17:31 Movies
drwxrwxrwx  2 1001 1001 0 2012-07-15 08:28 nzbs
drwxrwxrwx 54 1001 1001 0 2012-07-20 22:47 Television
drwxrwxrwx  2 1001 1001 0 2012-07-14 23:44 Untitled Folder
drwxrwxrwx  2 1001 1001 0 2012-07-19 13:40 Untitled Folder 2

```

The "Untitled" folders were created from this desktop using Nautilus.

However, when I try to "SAVE" or "SAVE AS" from within an application, like a word processor or internet browser, I get insufficient permissions error.

NB: I should add that if I "SAVE AS" to the desk top I can then drag and drop the file into the NAS directory via Nautilus or cp it.

What am I doing wrong?

THanks

---

### Post by papibe on 2012-07-20
Hi GuiGuy.

It looks like either the mount options are set for the incorrect user, or the there's a UID mismatch between your local user and the remote.

Could you post the result of this command?
```
id
```
Regards.

---

### Post by GuiGuy on 2012-07-20
> **papibe said:**
> Hi GuiGuy.

It looks like either the mount options are set for the incorrect user, or the there's a UID mismatch between your local user and the remote.


That was it. Typo in fstab.  I think I've been staring at the screen far too long :(

Many thanks.

---


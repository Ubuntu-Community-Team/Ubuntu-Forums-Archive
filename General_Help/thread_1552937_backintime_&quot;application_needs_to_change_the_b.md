---
title: "backintime: &quot;application needs to change the backup format&quot; ??"
date: 2010-08-14
forum: General Help
---

### Post by Pifilatakanemu on 2010-08-14
Hi, 
I used to make backups of my system with BackInTime. I updated to the newest beta version to use several profiles at once. It works with the two new profiles, but the main one that used to work does not work any more.

In the logs the error message says:

```
Aug 14 16:11:02 fabians-laptop backintime (root): INFO: The application needs to change the backup format. Start the GUI to proceed. (As long as you do not you will not be able to make new snapshots!)
Aug 14 16:11:02 fabians-laptop backintime (root): WARNING: Backup not performed
```

I can't figure out how to change the backup format.

The log view of BiT itself says:

```
========== Take snapshot (profile 1): Sa 14 Aug 2010 14:46:36  ==========

[E] Error: rsync: writefd_unbuffered failed to write 4 bytes to socket [sender]: Broken pipe (32)
[E] Failed to take snapshot 14.08.2010 14:46:36 !!!
```

Any suggestions?

Thanks!

edit:
It seems as if the beta stops working when the folder to save the snapshots is the same as it was with the previous version. I changed it and now it started the backup. Let's see how far he gets.

---


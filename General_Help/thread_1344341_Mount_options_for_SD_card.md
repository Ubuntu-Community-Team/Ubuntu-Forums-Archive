---
title: "Mount options for SD card"
date: 2009-12-02
forum: General Help
---

### Post by sgosnell on 2009-12-02
Well, I got carried away, and edited the properties of my built-in SD cardreader.  I changed the mount options to include noatime, and now it won't mount, with a dialog saying invalid mount options.  Anybody know where the properties for this are stored?  I've checked fstab and mtab, nothing there.  Until I can fix this, I can't mount an SD card.

Update: /home/user/.gconf/system/storage has two folders - volumes and drives.  Each had a folder named _org_freedesktop_Hal_devices_"other stuff" with a file named %gconf.xml, where "other stuff" is a long string with the UUID and other info.  Renaming the %gconf.xml and then rebooting solved the problem.  I'm still not certain exactly what the bad parameter was, but something was preventing the mount.  Apparently removing that file resets things to defaults, because a new file did not show up, and I suppose it is only generated via the Properties dialog for the drive.  In any case, the card is now mounted automatically when it is inserted.

---


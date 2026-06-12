---
title: "help please?"
date: 2011-09-25
forum: General Help
---

### Post by sharpertongue on 2011-09-25
I'm trying to install Safari with Wine but I'm getting this message...
The file '/****/****/Downloads/SafariSetup.exe' is not marked as   executable.  If this was downloaded or copied form an untrusted source,   it may be dangerous to run.  For more details, read about the  executable  bit.

How do I give permission to open it?

---

### Post by patryk77 on 2011-09-25
In nautilus (the file browser), right click the SafariSetup.exe file, select Properties

On the Permissions tab, check "Allow executing file as program"

Or from the terminal:
chmod +x ~/Downloads/SafariSetup.exe

[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by sharpertongue on 2011-09-25
thanks:)

---


---
title: "Where do you enable user sharing"
date: 2009-11-13
forum: General Help
---

### Post by garvinrick4 on 2009-11-13
Terminal: gksudo nautilus

(nautilus:5591): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed
Initializing nautilus-gdu extension

** (nautilus:5591): WARNING **: No marshaller for signature of signal 'UploadFinished'

** (nautilus:5591): WARNING **: No marshaller for signature of signal 'DownloadFinished'

** (nautilus:5591): WARNING **: No marshaller for signature of signal 'ShareCreateError'
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

---

### Post by garvinrick4 on 2009-11-13
Went alt/F2   entered gksudo nautilus opened nautilus as root.

traveled to folder I wanted to share-right clicked choose share.

---

### Post by mfhall on 2010-10-24
I know this is a late response, but I found this through google and it gave poor advice - it wasn't solved!

The error message is because the folder /var/lib/samba/usershares does not exist if samba is not installed. It doesn't matter.

As the folder doesn't exist, you can't solve it by travelling to the folder!

Either: 
1.    (Recommended) Ignore the error message - Nautilus still runs in super user mode (tested on 10.4.1 X64).
2.    Install Samba  - this creates the directory (empty) and the error message does not appear. Don't bother unless you actually want Samba for Windows sharing.

---


---
title: "gvfs-mount issue"
date: 2011-10-20
forum: General Help
---

### Post by kamaji792 on 2011-10-20
I'm having a problem with **gvfs-mount** when I use it to mount Samba shares.

I have a script for mounting several shares on my Lucid box.  If I do this shortly after turning the server on 6 of the 7 shares will mount without any problems the last always fails with the following message:
```
Error mounting location: DBus error org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)
```

I have searched the error message and tried re-setting the keyring password thing to no avail.

Additionally I can usually mount the share if I do the **Places** > **Connect to server...** and fill in the fields for my Samba share.

However if I don't do this just after my server starts I get a random number of mount failures.  This can be part sorted by running the script repeatedly or by **Places** etc...  But there is no guarantee that either of these options will work.  There have been occasions when I have failed to mount some of my shares.

Any thoughts? - k

For the record my script looks like:
```
#!/bin/bash
gvfs-mount smb://samba1/me
gvfs-mount smb://samba1/Share
gvfs-mount smb://samba1/HogShare
gvfs-mount smb://samba1/Download
gvfs-mount smb://samba1/Library
gvfs-mount smb://samba1/Photo
gvfs-mount smb://samba1/WWW
```

---

### Post by kamaji792 on 2011-12-13
Just for the record I think I have the solution (or work-around).

Instead of using:
```
gvfs-mount smb://<samba-server>/<share>
```

I find the following appears to work without any problems:
```
gvfs-mount smb://<user-name>@<samba-server>/<share>
```

Atb k

---


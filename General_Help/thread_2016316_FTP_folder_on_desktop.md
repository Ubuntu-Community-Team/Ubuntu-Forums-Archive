---
title: "FTP folder on desktop"
date: 2012-07-04
forum: General Help
---

### Post by msammels on 2012-07-04
OK, anyone know if I can display my FTP folder on my Ubuntu 12.04 / Unity desktop? I remember the option being around in GNOME 2.x

---

### Post by cipherboy_loc on 2012-07-04
Have a look at curlftpfs. Or if you have ssh, look into sshfs. I smbfs mount a NAS directory to ~/NAS (added it to /etc/fstab), and there is an option in nautilus (file manager) to mount it, so I would imagine it would show up (once mounted) on your desktop.

Script to mount, not sure how to add curlftpfs to fstab:
```

#!/bin/bash

curlftpfs ftp://ip.addr -o user=username /path/to/mount

```
Cipherboy

---


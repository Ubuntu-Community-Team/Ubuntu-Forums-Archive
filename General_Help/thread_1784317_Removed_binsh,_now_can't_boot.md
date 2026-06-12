---
title: "Removed /bin/sh, now can't boot"
date: 2011-06-16
forum: General Help
---

### Post by blimbo on 2011-06-16
Hi gang,

I was trying to point /bin/sh at /bin/bash but got the symbolic link the wrong way and wiped bash, so tried to reinstall it but apt gave me problems. So I tried rebooting, but it fails to with errors like this:

init: Failed to spawn plymouth main process: unable to execute: no such file or directory

I'm pretty sure this is related to the lack of /bin/sh

So how can I tinker with the grub boot arguments and give it /bin/dash or something instead? I'm running 10.10 in a VM (Parallels) so don't have access to the filesystem from elsewhere (as far as I know) :-(

Cheers,
Tim

---

### Post by blimbo on 2011-06-16
Ah fixed it, booted into an install disc (well, .iso) and copied the links back.

Cheers,

Tim

---

### Post by sisco311 on 2011-06-16
EDIT: Never mind. I'm glad you figured it out. 

Don't forget to mark this thread as [SOLVED]. Thanks!
[/EDIT]

Hold down the shift key during the boot process. When the Grub propt appears, highlight the *Recovery Mode* entry, then press **e** for edit. Remove the **ro sinlge** boot options from the end of the **linux** line and append it with **rw init=/bin/dash**. Press Ctrl+x to boot.

Once you get a dash prompt remount the root partition as rw:
```
mount -o remount,rw /
```

Restore the symlink and reboot...

---


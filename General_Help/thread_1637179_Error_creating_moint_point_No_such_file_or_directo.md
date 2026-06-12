---
title: "Error creating moint point: No such file or directory"
date: 2010-12-04
forum: General Help
---

### Post by glomboi on 2010-12-04
When plugging in a USB Flash Card (via Flash Card Reader) I get the following error:

> Unable to mount 2.0 GB Filesystem
Error creating moint point: No such file or directory

(Yes, mount is misspelt on the actual error too!)

Similar problems have been posted elsewhere giving the solutions that /media is missing (it isn't in my case) and to mount it manually.

Trying to mount manually, I tried to create a folder 'flash' in /media but got the following error:

> mkdir: cannot create directory `flash': No such file or directory

I'm guessing this is the root of the problem.

I've checked permissions on /media and tried 'chmod'ing to various settings (current and default is 755).

Any help would be greatly appreciated!

Also, a small quirk, when booting with the device connected, Nautilus displays the device as mounted for a few seconds then it disappears again.

---

### Post by SeijiSensei on 2010-12-04
You have to be root to create a directory under /media.  Did you use "sudo mkdir /media/flash"?

---


---
title: "Lost root password"
date: 2012-05-20
forum: General Help
---

### Post by blackoutmikey on 2012-05-20
Hi

I've lost the root password to my system (or, I've lost all my passwords to the system, and I need a root account for reseting it so I can use sudo). The root account was locked with "passwd -l" so I tried booting into recovery mode, but I later discovered that I needed a password for dropping into root shell. I then edited the startup stuff (pressed "e" when the recovery option was highlighted) and on the line with "linux" on I removed ro single and replaced it with rw init=/bin/bash. This should work, but it seems like it locked itself up after displaying:
```
cannot set terminal process group (-1) inappropriate ioctl for device ubuntu
```
And gives me a blinking root terminal, which I can't do anything on, seems like the entire kernel is locked. How do I sort this? Is there any other way to gain entry to the system? I only have KVM access, and I don't know if the DC's remote hands will do something to the actual machine.

I'm on a Ubuntu Server 12.04 install with the stock kernel.

Thanks in advance.

---

### Post by jpeddicord on 2012-05-20
If you're able to mount your FS from a recovery image (your VPS host may provide a way to do this), you could try manually "locking" the root account by removing the password on it. This will make recovery mode sign in as if there wasn't a password ever set.

To do this, edit /etc/shadow and set root's password, the second field between the colons, to "!" (no quotes). For example, mine looks like ```
root:!:15310:0:99999:7:::
``` Recovery mode will no longer prompt for a password. You may want to set your root password again afterwards, though. :)

If you're unable to mount your disk/disk image, you may be stuck messing with boot options again. Try /bin/sh instead of /bin/bash as well, you might have more luck.

---

### Post by blackoutmikey on 2012-05-21
Hi. Tried with /bin/sh, it locked after some "/bin/sh: 0 can't access tty; job control turned off". I guess my only option then is to use a recovery disk? Should I try editing the standard kernel boot options and not the recovery one?

---


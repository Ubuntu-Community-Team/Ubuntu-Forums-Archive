---
title: "fsck won't run"
date: 2010-12-12
forum: General Help
---

### Post by meanmrmustard on 2010-12-12
During the post sequence my Hardy installation tries to run fsck on /dev/sb3 - which is the home partition. It fails at 10% or so and tells me to enter the root passwd to run it manually, or Ctrl D to continue normal boot.
It then ignores any keystrokes for the passwd but does respond to Ctrl D and then boots to the desktop.

I then drop to single user mode and try again but gives this message:

fsck: fsck.swap: not found
fsck: Error 2 while executing fsck.swap for /dev/sdb3

Eh? sdb3 is *_not_* the swap partition


Google is usually my friend but not today, everything I find is RAID related.

anyone have a clue?

---

### Post by tredegar on 2010-12-12
The password is not being ignored, just not echoed to the terminal. This is normal, so just type it and press return to get to a root shell.

Make sure /dev/sdb3 is unmounted, then run fsck on it (I am *assuming* it is an ext4 partition, adjust the fsck command if not):
```
umount /dev/sdb3
fsck.ext4  -f /dev/sdb3
```
Good luck.

---

### Post by meanmrmustard on 2010-12-12
> **tredegar said:**
> The password is not being ignored, just not echoed to the terminal. This is normal, so just type it and press return to get to a root shell.

Actually I'm pretty sure it is being ignored.
When I enter the psswd, it returns with the same message to enter the psswd to enter maintenance shell as root or type CTRL D to continue, and then just sits there doing nothing - until I type Ctrl D.

The partition was unmounted before both attempts.

---

### Post by tredegar on 2010-12-12
If it is being ignored, something is wrong, but my system is different, because I have done the non-ubuntu thing and set a root password (sometimes, like your current situation, I need to login as root and not have **/home** mounted).

Try booting to rescue mode from grub, choose the root shell option.
Then run the above commands.

---


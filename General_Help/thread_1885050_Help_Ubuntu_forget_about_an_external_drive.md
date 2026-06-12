---
title: "Help Ubuntu forget about an external drive"
date: 2011-11-22
forum: General Help
---

### Post by gwis on 2011-11-22
Long ago, I mounted an external USB drive, to copy some data.  It was a one-time thing. But, ever since, when I boot I get a message that /media/DRV2_VOL1 cannot be found.  I probably forgot to unmount the drive before I disconnected it.

I can successfully boot by telling ubuntu to skip the drive, but is there anyway I can get rid of the message?

I tried deleting the entry for the absent drive in /media, but that did not help.

Somewhere, ubuntu remembers that drive.  How can I make it "forget"?

---

### Post by 2F4U on 2011-11-22
Is it mounted through /etc/fstab? If yes, you need to change that file.

---

### Post by gwis on 2011-11-22
2F4U !  Thanks !  That's where it was hiding.  a little sudo vim and all is well again.
:D

---


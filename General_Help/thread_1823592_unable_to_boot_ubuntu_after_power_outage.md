---
title: "unable to boot ubuntu after power outage"
date: 2011-08-12
forum: General Help
---

### Post by kelean on 2011-08-12
My computer was on when the power went out.  I am not able to boot into ubuntu 11.4 install since that happened.  I also have debian 6 and ubuntu 11.10 installed on the same machine and both boot just fine.

The machine boots as normal but stops with the line "disconnected from Plymouth". After the machine just sits there with a blinking cursor.  I cannot start another terminal.  Is my only option to reinstall.

I am stuck so amy help would be greatly appreciated.

Kelean

---

### Post by CatKiller on 2011-08-12
You can probably run a fsck on the damaged partition from a live cd or from one of your other environments.

---

### Post by kelean on 2011-08-12
CatKiller I ran fsck from a liveusb and fsck came back clean.  Retried and it would not boot.

---

### Post by CatKiller on 2011-08-12
Sorry, I don't know what else to suggest. You can probably get to a root shell from the Grub menu's Recovery mode option, but I don't know what would be good to run there.

---

### Post by kelean on 2011-08-12
Recovery mode will not either.  I tried entry’s  for both kernels.  Looks like a reinstall is in order.  Thanks for the help.

---

### Post by JC Cheloven on 2011-08-12
Before reinstalling, I'd suggest to check again: fsck reporting no errors is quite strange in your situation. Please see how much similar is the following compared to what you did:

- Start a live session.
- Run "sudo fdisk -l" at a terminal to be sure what's the partition you want to check and repair. It will be somehing as /dev/sd??, where ?? are a letter and a number (ex: /dev/sda5). Also "sudo blkid" can help if you're still unsure which partition is the one containing ubuntu (this one lists the partition labels as well).
- Run "sudo fsck /dev/sd??" (replace ?? as apropriate).

---

### Post by kelean on 2011-08-13
That is how I did it.  I retried just to be sure and it still came back clean.  Thanks for the help, Kelean.

---


---
title: "HELP - Several PCs don't start anymore...today..."
date: 2011-06-25
forum: General Help
---

### Post by Romu on 2011-06-25
hi all,
This seems to be a kind of epidemic.

We are at least 3 people on the French Ubuntu forum with the same issue which has just appeared...today.

We start our laptops and they don't boot, we have just the message:

"* Stopping System V runlevel compatiblity      [OK]"
...and a blinking cursor.

That's all, seems we are stuck here. So any help would be greatly appreciated. Thanks.

---

### Post by Romu on 2011-06-25
After some googling and search here, it appears the problem may come from fsck.

Any help?

Thanks.

---

### Post by tgalati4 on 2011-06-25
Find a LiveCD and boot from it.  Open a terminal:
sudo fdisk -l
sudo fsck /dev/sda2

Your boot partition may be different.

---

### Post by Romu on 2011-06-25
Hi and thanks for help.

My boot partition is sda1, but sudo fsck /dev/sda1 doesn't change anything.

I think I should re-install.

---


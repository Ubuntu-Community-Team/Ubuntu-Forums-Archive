---
title: "How to force Live CD to use swapfile?"
date: 2011-07-23
forum: General Help
---

### Post by myitanium on 2011-07-23
I create liveusb using Ubuntu. The problem is Ubuntu always use my swap partition, but i want to make it use my swapfile which is located on the flashdisk.
I know that after login, i can add swap. But that's not the point, i want Ubuntu use swap file in flashdisk since booting.

Anyone know how to do it?

---

### Post by CatKiller on 2011-07-23
Using the swap partition would be better, since the flash memory has a limited number of write cycles.

I haven't tried changing the live environment, but you'll want to add an entry to /etc/fstab, as you would when specifying a swap file normally. You might find that [this page]("https://wiki.ubuntu.com/LiveUsbPendrivePersistent") has useful information on how to customise your liveusb environment.

---

### Post by myitanium on 2011-07-24
Thanks for your reply. Very helping article.
I want to force using swapfile because sometimes, i need to run the flasdisk in PC without swap partiton and limited memory. And in that case i want Ubuntu to use swapfile.

---

### Post by CatKiller on 2011-07-24
When you get your swapfile set up you could enable it manually for those instances when there's no swap partition with the swapon command.

---


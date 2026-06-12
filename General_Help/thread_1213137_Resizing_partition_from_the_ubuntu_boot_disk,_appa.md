---
title: "Resizing partition from the ubuntu boot disk, apparently failing"
date: 2009-07-14
forum: General Help
---

### Post by ZankerH on 2009-07-14
Trying to install ubuntu on a friend's laptop, booted from the live CD and fired up gparted to make some space. It's been resizing a 150GB NTFS partition with 130GB free space down to 50GB for 20 minutes now, so I think the resize failed. Cancelling will obviously cause severe filesystem damage. What should I do?

---

### Post by Finalfantasykid on 2009-07-14
The partitioning process takes a really really long time.  Just wait it out and see what happens.  If nothing has happened after a couple of hours, then maybe get concerned.

---

### Post by merlinus on 2009-07-14
Wait.  It takes a long time for these operations.

---

### Post by ZankerH on 2009-07-14
Thanks for the advice, looks like it's working now, there's a progress bar and it's moving. Gparted decided to resize the partition *and* move it in front of the 1.0 MiB unallocated space for some reason, that's why it's taking so long. I was getting really nervous here, since the person I'm installing ubuntu for doesn't submit to the religion of Regular Backups.

---


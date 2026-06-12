---
title: "primary and backup superblock"
date: 2011-09-01
forum: General Help
---

### Post by Ruy Benton on 2011-09-01
Hi,

I have a UBUNTU 11.04 with two ext4 partitions.

And I fsck the unmounted part. to see if everything is ok.

"fsck.ext4 -n /dev/sda1" and everything ok.

Next step "dumpe2fs /dev/sda1" and write the backup superblock.

"fsck.ext4 -n -b 32768 /dev/sda1"                  (block size 4096)

and lots of Free block wrong and 
"Group descriptor xxxxx checksum is invalid.  IGNORED."



Start with lots of different live distribution and the same behaviour.

Why the first (0) Superblock is ok ... with a backup lots of error?

Best regards,
Ruy

---


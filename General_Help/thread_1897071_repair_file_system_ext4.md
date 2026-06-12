---
title: "repair file system ext4"
date: 2011-12-18
forum: General Help
---

### Post by apophis zeudap on 2011-12-18
Hello can someone tell me how long it take to do a 
e2fsck.ext4 -y -b block# /dev/sdb1 on a 2TB hard drive 
Cause it s like a day that is running and like an hour with this message.

Error reading block 9248 (Attempt to read block from filesystem resulted in short read) while getting next inode from scan.  Ignore error? yes

Force rewrite? yes

Inode 127210 has INDEX_FL flag set but is not a directory.
Clear HTree index? yes

Inode 127210 should not have EOFBLOCKS_FL set (size 8589934592, lblk -1)
Clear? yes

Inode 127210, i_blocks is 149555056183300, should be 0.  Fix? yes

Inode 127209, i_size is 18446612149494056963, should be 0.  Fix? yes

Inode 127209, i_blocks is 281474976679940, should be 0.  Fix? yes

---


---
title: "kern.log non-stop filling with eCrypt error messages - how to repair?"
date: 2012-08-02
forum: General Help
---

### Post by dutchslab on 2012-08-02
Hi-

When I tail -f my kern.log, this message is being writtent to it non-stop:

Aug  2 11:11:09 dually kernel: [ 3027.172722] Valid eCryptfs headers not found in file header region or xattr region, inode 3964173
Aug  2 11:11:09 dually kernel: [ 3027.172724] Either the lower file is not in a valid eCryptfs format, or the key could not be retrieved. Plaintext passthrough mode is not enabled; returning -EIO


How can I fix this?

I am on Ubuntu 12.04 on a Thinkpad W520 on SSD.

---

### Post by dutchslab on 2012-08-02
I found the solution:

[https://bugs.launchpad.net/ecryptfs/+bug/911507/comments/19](https://bugs.launchpad.net/ecryptfs/+bug/911507/comments/19)

After finding the file, I deleted it, and the error went away. Would have been great to repair the file, but luckily it wasn't needed. Maybe someone knows how to repair it as well?

---


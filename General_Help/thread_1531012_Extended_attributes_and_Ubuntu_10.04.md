---
title: "Extended attributes and Ubuntu 10.04"
date: 2010-07-14
forum: General Help
---

### Post by derek71 on 2010-07-14
I have installed Ubuntu 10.04 server to act as a Samba server, and I want to use extended attributes to store the Windows time stamp information.

On the Samba side I enabled extended attributes, and I have user_xattr included in the mount point for the partition containing the Samba shares.

When I test extended attributes (user.name) with setfattr and getfattr, I get an error message indicating that the operation is not supported.

I also checked the settings in the kernel and extended attributes are enabled for ext3 and ext4.

I wanted to find out if this problem requires an update to the kernel (current version: 2.6.32-21), or if ext3/ext4 extended attributes are not supported fully?

---


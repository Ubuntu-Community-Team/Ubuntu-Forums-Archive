---
title: "custom/manual mount of root partition in boot hook"
date: 2011-04-04
forum: General Help
---

### Post by imraven52 on 2011-04-04
First time post, please excuse the miss-post.

The quick of it is: what is the best way, or where should I start in customizing how the OS mounts the root partition on boot.

Long version.  I'm experimenting with the ZFS filesystem per [http://zfsonlinux.org/](http://zfsonlinux.org/).  So far my testing is proving it quit solid in Ubuntu/Linux.  However, I'd like to take it a step further and make it my root partition.  I've gone as far as adding the userland utils for ZFS to the initramfs and even have it detecting and mounting the filesystem on boot.  The next step is figuring out how to remove whatever hook is causing the other root to mount and allowing ZFS to assume the role.

Thoughts?

Thanks,

Brandon

---


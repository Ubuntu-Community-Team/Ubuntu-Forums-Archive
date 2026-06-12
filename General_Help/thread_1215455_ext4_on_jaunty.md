---
title: "ext4 on jaunty"
date: 2009-07-17
forum: General Help
---

### Post by metalmaniac248 on 2009-07-17
could anyone tell me if there is any real point in upgrading to ext4 on Jaunty instead of just waiting for karmic koala,

and is there any difference in using a method like this 

> Converting ext3 to ext4

To convert an existing ext3 filesystem to use ext4, use the command

$ tune2fs -O extents,uninit_bg,dir_index /dev/DEV

WARNING: Once you run this command, the filesystem will no longer be mountable using the ext3 filesystem!

After running this command, you MUST run fsck:

$ fsck -pf /dev/DEV

NOTE: by doing so, new files will be created in extents format, but this will not convert existing files. However, they can be transparently read by Ext4.

WARNING: It is NOT recommended to resize the inodes using resize2fs, as this is known to corrupt some filesystems.

to convert to ext4 over just doing a clean install and selecting ext4

---

### Post by philinux on 2009-07-17
To be honest if your Jaunty install is working fine I would leave well alone. 

I'm dual booting, have been for ages. Always have latest stable ubuntu on disk one and development cycle, karmic, on disk two. It's important to have one stable system.

Just reinstalled karmic alpha3 on disk 2 with ext4 and of course this gets grub2 now too. Boot up time to login is faster with ext4. But from a cold boot up my router takes the longest time, to get net up lol.

---

### Post by binbash on 2009-07-17
that method does not convert existing files.It is best to do a clean install.Wait for Karmic Koala.

---

### Post by metalmaniac248 on 2009-07-17
thanks just wanted some opinions i thnk i shall wait for koala

---

### Post by metalmaniac248 on 2009-07-17
oh and you know when we upgrade to karmic in october will it automatically upgrade to ext4?

---

### Post by kpkeerthi on 2009-07-17
Jaunty's kernel has EXT4 fixes backported from Karmic's.

---


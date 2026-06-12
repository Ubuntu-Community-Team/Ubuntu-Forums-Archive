---
title: "Remastersys help"
date: 2010-08-29
forum: General Help
---

### Post by TimEnid on 2010-08-29
I just performed a backup and i get the message "the compressed filesystem in larger than iso9660 specification allows for a single file. You must try to reduce the amount of data you are backing up and try again".

what does this mean? I just want to back up my system to my external hd. 

also, how do i choose where the backup will be installed?

---

### Post by mikewhatever on 2010-08-29
[http://en.wikipedia.org/wiki/ISO_9660#The_2.2F4_GiB_file_size_limit](http://en.wikipedia.org/wiki/ISO_9660#The_2.2F4_GiB_file_size_limit)

I guess you should use another backup tool. Clonezilla or fsarchiver come to mind.

---

### Post by inameiname on 2010-08-29
I'm afraid you are limited on the maximum size of a Remastersys backup. I believe it's at 4.4 GB. You need to lose some to accommodate that restriction.

---

### Post by TimEnid on 2010-08-29
> **mikewhatever said:**
> [http://en.wikipedia.org/wiki/ISO_9660#The_2.2F4_GiB_file_size_limit](http://en.wikipedia.org/wiki/ISO_9660#The_2.2F4_GiB_file_size_limit)

I guess you should use another backup tool. Clonezilla or fsarchiver come to mind.

can a bootable cd be made with fsarchiver?

---

### Post by mikewhatever on 2010-08-29
No, I don't think so. However you can restore from Clonezilla's and Fsarchiver's backups just the same.

---


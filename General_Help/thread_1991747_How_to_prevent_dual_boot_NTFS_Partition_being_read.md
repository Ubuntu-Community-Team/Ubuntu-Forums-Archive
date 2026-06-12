---
title: "How to prevent dual boot NTFS Partition being read?"
date: 2012-05-30
forum: General Help
---

### Post by listerdl on 2012-05-30
I dual boot and would rather not have my NTFS Parition accessible via my ubuntu ext4 partition.

Is there a way to permamently unmount this?

Thanks

---

### Post by dcstar on 2012-05-31
> **listerdl said:**
> I dual boot and would rather not have my NTFS Parition accessible via my ubuntu ext4 partition.

Is there a way to permamently unmount this?

Thanks

You put it into /etc/fstab with the "noauto" option.

---

### Post by listerdl on 2012-06-01
> **dcstar said:**
> You put it into /etc/fstab with the "noauto" option.

Thanks...

can that file be password protected - or rather can /etc/ be password protected?

---

### Post by listerdl on 2012-06-02
Is there a more "permanent" way to separate your partitions - I'd prefer it if my work data was kept in Windows where it belongs (I dual boot).

I would prefer to keep ubuntu for personal stuff - the fact that my NTFS Partition is so easily mountable means that accidentally or in malice my windows partition could also be viewed. Can I completely block that?

Does placing my NTFS Partition in a "noauto" option using /etc/fstab render that partition "non accessible"?

I guess the answer is yes and no. No because if a hacker got control of the machine (not physically) then he could re-activate the noauto - right?

Thanks!!!!!

---


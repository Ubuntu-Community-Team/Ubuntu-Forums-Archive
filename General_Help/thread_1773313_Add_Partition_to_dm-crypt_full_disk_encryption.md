---
title: "Add Partition to dm-crypt full disk encryption"
date: 2011-06-01
forum: General Help
---

### Post by NertSkull on 2011-06-01
So, I set up a full disk encryption on my main partition using dm-crypt/LUKS when I installed a while back.  I have the root encrypted, along with the swap space (but not the boot partition).

I have a fourth partion that I did not add to the encrypted hard disk.

My question is how can I add that partition now?  So that when I turn on the computer and I enter the password for the swap and root, it would also unlock the 4th data partition.

I would assume I have to add it to the logical volume as a new logical partition that gets encrypted as part of that group.  Is that right?

Or does it just need to be encrypted and added to the fstab?

I'm a little confused on how to go about doing this.  The 4th partition is empty right now.  So how can I add it to the already encrypted file systems.  (I don't really want to just expand the existing file systems, but actually add the partition, as a separate partition.)

---


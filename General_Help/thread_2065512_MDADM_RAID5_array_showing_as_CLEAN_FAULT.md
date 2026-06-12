---
title: "MDADM RAID5 array showing as CLEAN FAULT"
date: 2012-10-02
forum: General Help
---

### Post by datr on 2012-10-02
A drive dropped out of my raid 5 array yesterday. It looks like the reason was due to a bad controller so I switched it out and attempted to re-add the drive but mdadm claimed it couldn't do it. So I zerod the superblock and just added the drive normally and left it to resync.

When I came to check on the array this morning I was unable to mount it at all and it's now showing as CLEAN FAULTY with two drives missing. The two missing drives are listed as spare and faulty spare.

Is there anything I can do in this situation or is the array gone?

---

### Post by datr on 2012-10-02
OK I was able to recreate the drive by forcing mdadm to ignore that one of the spares was fauly by ussing --assemble --force and I can now access the array.

I'm currently creating a new off-site backup of my most important files to make sure there's nothing I'm missing but my question now is what should I do next.

The 3 drives I have are each 3TB and they don't contain anything that I wouldn't be that fussed about if I lost but RAID 5 seems to be tempermental at best. Is there a better alternative and if not how do I get my array back to a CLEAN state?

---


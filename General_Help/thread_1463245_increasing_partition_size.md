---
title: "increasing partition size"
date: 2010-04-26
forum: General Help
---

### Post by wcutrombonekid on 2010-04-26
I shrunk my windows partition and moved it over and got it booting again

now, i have a big chunk of unallocated space that I would like to give to my ubuntu partition.  Problem is, it wont let me expand it into that space, i have searched and havn't found this problem from anyone who isn't using a mac.

---

### Post by oldfred on 2010-04-26
Your ext4 is a logical inside the extended partition. 
You should extend the sda3 extended partition into the free space then you can expand the ext4 partition inside the extended partition.

---

### Post by srs5694 on 2010-04-27
In addition to oldfred's response (which is correct), you must unmount the Linux partition in order to expand it. This means you must boot from an emergency disc, such as [System Rescue CD](http://www.sysresccd.org/) or [PartedMagic.](http://partedmagic.com) (I believe the Ubuntu Live CD should also work, but I generally use System Rescue CD or PartedMagic for this sort of thing.)

One other comment: Instead of expanding your Linux root (/) partition, you should give serious consideration to creating a separate /home partition. This will give you much greater flexibility about upgrading or re-installing Ubuntu, or even switching to another distribution if you choose to do so in the future. There are quite a few tutorials on the Web about this; try Googling something like "Linux creating /home partition" to find them.

---

### Post by wcutrombonekid on 2010-04-27
> **srs5694 said:**
> In addition to oldfred's response (which is correct), you must unmount the Linux partition in order to expand it. This means you must boot from an emergency disc, such as [System Rescue CD]("http://www.sysresccd.org/") or [PartedMagic.]("http://partedmagic.com") (I believe the Ubuntu Live CD should also work, but I generally use System Rescue CD or PartedMagic for this sort of thing.)

One other comment: Instead of expanding your Linux root (/) partition, you should give serious consideration to creating a separate /home partition. This will give you much greater flexibility about upgrading or re-installing Ubuntu, or even switching to another distribution if you choose to do so in the future. There are quite a few tutorials on the Web about this; try Googling something like "Linux creating /home partition" to find them.


I never thought about that, but it makes a lot of sense, i'll check it out

---

### Post by oldfred on 2010-04-27
I used this:
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)
Sometimes there are dmrc errors or permission errors and this has how to correct them:
[https://help.ubuntu.com/community/dmrcErrors](https://help.ubuntu.com/community/dmrcErrors)

[http://linuxtipstricks.wordpress.com/2008/10/05/how-to-create-a-separate-home-partition-in-linux-ubuntu-opensuse-mandriva-gentoo-fedora-and-so-on/](http://linuxtipstricks.wordpress.com/2008/10/05/how-to-create-a-separate-home-partition-in-linux-ubuntu-opensuse-mandriva-gentoo-fedora-and-so-on/)
[http://embraceubuntu.com/2006/01/29/move-home-to-its-own-partition/](http://embraceubuntu.com/2006/01/29/move-home-to-its-own-partition/)

the last two links were I think, one's that srs5694 had found and they looked ok.

---


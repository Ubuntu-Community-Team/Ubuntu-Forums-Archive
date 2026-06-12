---
title: "Does an ext4 filesystem being used only for data storage require a swap space?"
date: 2011-05-06
forum: General Help
---

### Post by SlimBiggins on 2011-05-06
Hello,

I am running a dual boot system with Win7 on /dev/sda and Ubuntu 10.10 on /dev/sdb

I also have a 250 GB disk I use for storing backup data, /dev/sdc

The two logical partitions on /dev/sdc (/dev/sdc2 and /dev/sdc5) each take up 2.86 GB and I would like to free up that space if possible.

Since the filesystem on /dev/sdc doesn't have an OS on it, does it still require that those two logical partitions exist?

I've google'd all over for an answer to this, but couldn't find anything even close.

Any help is always greatly appreciated

Thanks
- SlimBiggins

---

### Post by YesWeCan on 2011-05-06
Hi.
The swap space for linux can be located anywhere. You should have one on sdb already. If so, and if your sdb filesystem has no links to sdc then you should be able to do whatver you want with sdc. You can confirm this by disconneting sdc and after rebooting nto linux on sdb check everything is normal.

---

### Post by deathadder on 2011-05-06
A short answer is just because it's got a filesystem doesn't mean it needs a swap.

As mentioned by YesWeCan swap space can be on any hard drive not that you always need one anyway but that's a different point. If you've got a swap partition on your existing drive (sdb) then you can partition and format your drive (sdc) as you like. Likewise, if you don't have a swap partition at the moment then go ahead and do as you want.

---

### Post by SlimBiggins on 2011-05-06
Thanks for the help guys. I should have been more specific about the location of the swap partition that is in use by Ubuntu. 

The Ubuntu OS is on /dev/sdb1 and its swap space is located at /dev/sdb5

My backup disk is /dev/sdc and I was inquiring about sdc's swap space.

I'm going to delete the swap on /dev/sdc to free up the space, but I still need to resize the partition /dev/sdc1

I was just a little leery on deleting a partition and not knowing whether or not it was necessary to keep. 

I will post when successfully finished and set the thread as solved.

Thanks again,
- SlimBiggins

---

### Post by YesWeCan on 2011-05-06
> **SlimBiggins said:**
> Thanks for the help guys. I should have been more specific about the location of the swap partition that is in use by Ubuntu. 

The Ubuntu OS is on /dev/sdb1 and its swap space is located at /dev/sdb5

My backup disk is /dev/sdc and I was inquiring about sdc's swap space.

I'm going to delete the swap on /dev/sdc to free up the space, but I still need to resize the partition /dev/sdc1

I was just a little leery on deleting a partition and not knowing whether or not it was necessary to keep. 

I will post when successfully finished and set the thread as solved.

Thanks again,
- SlimBiggins
Always err on the cautious with this stuff, no shame in asking. Keep asking.
Will you be repartitioning using a live CD or using the sdb Unbuntu?
This is pedantic but just for your information, when the Ubuntu sdb boots it will recognize all the swap partitions on all your disks and note them for its use. So it is, in theory, possible to break a running app if, say, Ubuntu has used some of the swap space on sdc and then you go and delete sdc swap. However, this is extremely unlikely unless you are running huge RAM consuming applications at the same time.

You can check how much swap space you are using in the System Monitor. You can list the swaps in use 'swapon -s' and you can disable a swap or all swaps using swapoff.

This does raise a question for me: if there are multiple swap partitions which order are they used in?

---

### Post by blind2314 on 2011-05-06
> **YesWeCan said:**
> Always err on the cautious with this stuff, no shame in asking. Keep asking.
Will you be repartitioning using a live CD or using the sdb Unbuntu?
This is pedantic but just for your information, when the Ubuntu sdb boots it will recognize all the swap partitions on all your disks and note them for its use. So it is, in theory, possible to break a running app if, say, Ubuntu has used some of the swap space on sdc and then you go and delete sdc swap. However, this is extremely unlikely unless you are running huge RAM consuming applications at the same time.
 
You can check how much swap space you are using in the System Monitor. You can list the swaps in use 'swapon -s' and you can disable a swap or all swaps using swapoff.
 
This does raise a question for me: if there are multiple swap partitions which order are they used in?
 
It's my understanding that they are all treated as one big "pool". So if you have swap on partitions sda/sdb/sdc, they won't necessarily be used in a particular order, but rather have the data striped across them. I'm going to try and dig around for proof of what I just said, but I'm *fairly* certain I'm correct.

---

### Post by SlimBiggins on 2011-08-26
Sorry guys for the delayed response. I lost the aforementioned PC in an electrical storm. Needless to say, I no longer have that filesystem configuration anymore.

However, there is still one question that remains.

If I create an EXT4 filesystem with a swap space, how can I go about *resizing* the ext4 partition over top of the deleted swap.

I've googled for a while on this one and had to come back for some closure.

All help always appreciated,
-SlimBiggins

---

### Post by wojox on 2011-08-26
Use a Live-CD to mount the drive and open Gparted, turn off swap, delete it, and expand the partition.

---

### Post by SlimBiggins on 2011-08-26
Thanks for the speedy response. I think we can mark this one as SOLVED. I didn't know that GParted could resize, but I'm taking your word.

Thanks again everybody!

---


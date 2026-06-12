---
title: "How do I format entire partition to be used by Ubuntu?"
date: 2010-05-24
forum: General Help
---

### Post by lulabelf on 2010-05-24
I have succeeded in deleting my former Windows XP partition and it is now unallocated.  How do I allocate all of the space to Ubuntu?

Attached is my Gparted screen.  There was an error when booting Ubuntu initially and I was never able to dual boot.  XP is gone now.   I want Ubuntu to have all the space.  Thanks.

---

### Post by wilee-nilee on 2010-05-24
If you just want ubuntu and nothing on the hard saved as of now just choose the install on the whole HD option in the install. If you want a separate home That can be kept through upgrades then somebody else will be able to help you there I don't use that method, so I'm not familiar with it.

AS it is you have deleted XP but you still have partitions, which doesn't matter if your going to over write the whole HD.

If the ext4 within the logical and having a swap is what you want to keep, and then install in the other partition it would be helpful to know what you have and what you want to install.

---

### Post by ali999 on 2010-05-24
what was the error exactly if you can recall? i think it might be an issue with the two ext partitions. I usually just setup one partition as ext4 and use that as the mount point (/). I am not sure which one you have installed ubuntu on...the ext4 seems to be taking too much space for just linux so I am not sure. I would recommend just reinstalling again with just one partition. 

also if you want to setup a dual boot, i have found this guide useful in the past [http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm](http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm).

---

### Post by lulabelf on 2010-05-25
> **wilee-nilee said:**
> If you just want ubuntu and nothing on the hard saved as of now just choose the install on the whole HD option in the install. If you want a separate home That can be kept through upgrades then somebody else will be able to help you there I don't use that method, so I'm not familiar with it.

AS it is you have deleted XP but you still have partitions, which doesn't matter if your going to over write the whole HD.

If the ext4 within the logical and having a swap is what you want to keep, and then install in the other partition it would be helpful to know what you have and what you want to install.


Thanks for your response.  After months of toying wth Ubuntu, I just used a live CD and started over.  All my issues are resolved.

---

### Post by lulabelf on 2010-05-25
> **ali999 said:**
> what was the error exactly if you can recall? i think it might be an issue with the two ext partitions. I usually just setup one partition as ext4 and use that as the mount point (/). I am not sure which one you have installed ubuntu on...the ext4 seems to be taking too much space for just linux so I am not sure. I would recommend just reinstalling again with just one partition. 

also if you want to setup a dual boot, i have found this guide useful in the past [http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm](http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm).


Thanks for response and for excellent step by step guide.   I just used a live CD and installed Ubuntu again.  All my issues have been corrected.

---


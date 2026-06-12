---
title: "extending my ubuntu partition"
date: 2011-09-13
forum: General Help
---

### Post by rmcellig on 2011-09-13
i had win7 dual booting on my laptop with ubuntu. i just deleted my win7 partition and would like to extend my ubuntu partition to take up all this unallocated space. what are my options?

---

### Post by nothingspecial on 2011-09-13
Well you could move your Ubuntu partition to the left and then resize it to use the space.

But before you do that, consider making a new ext4 partition and using it for /home or data.

[http://psychocats.net/ubuntu/separatehome](http://psychocats.net/ubuntu/separatehome)

Make backups because messing about with partitions always carries the risk of data loss.

---

### Post by Mark Phelps on 2011-09-13
IF you do resize, instead of adding a new partition, be aware that you have to resize the Extended partition first; then, the Linux partition inside that.

---

### Post by Wim Sturkenboom on 2011-09-13
With 200GB in the first partition,I'll second nothingspecial's suggestion for a separate home partition.

---

### Post by PayPaul on 2011-09-29
I may have a related question. I installed Ubuntu 11.04 using Wubi. The partition it's installed in is the 3rd partition that existed prior to the Ubuntu install on my main drive. Win7 is on the 1st partition. The Wubi program gives a maximum of 30 gbs over to Ubuntu. I'd like to extend that size to use the rest of that 3rd partition. As of now I don't even see the free space on that that 3rd partition. Is this possible or should I just wait until I reinstall Ubuntu using a livecd?

---


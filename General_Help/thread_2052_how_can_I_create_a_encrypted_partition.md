---
title: "how can I create a encrypted partition"
date: 2004-10-25
forum: General Help
---

### Post by rupert on 2004-10-25
Hi,
I wanna setup a encrypted harddrive, 
i know that there is a cryptofs.
Is that the general way to set a encrypted filesystem up?
Can you please point me to a recent howto, maybe in german.

thx
rupert

---

### Post by flygmaskin on 2004-10-25
[QUOTE=rupert]Hi,
I wanna setup a encrypted harddrive, 
i know that there is a cryptofs.
Is that the general way to set a encrypted filesystem up?
Can you please point me to a recent howto, maybe in german.

thx
rupert[/QUOTE]
 [http://www.fedoranews.org/alex/tutorial/crypto](http://www.fedoranews.org/alex/tutorial/crypto)

The tutorial is for fedora, but I think it works just fine on Ubuntu as well.

---

### Post by rupert on 2004-10-25
thx,
which filesystem would be the best and safest,
i read that reiserfs4 is supported,
or would it be better to use ext3 or the older reiserfs?

PS:
I just used ext3 for a test, its up and running.
I use this line in fstab

/dev/sdc1               /mnt/crypto             ext3 loop=/dev/loop0,encryption=serpent,noauto,user 0 0

But it doesnt show up in the nautilus drives sektion,
would be nice to click it there and enter the password.

mmh, i cant mount it with mount /mnt/crypto.
ioctl: LOOP_SET_FD: Das Gerät oder die Ressource ist belegt

I got the line in the fstab from a different howto, maybe something changed.

---

### Post by rupert on 2004-10-25
bump

---

### Post by flygmaskin on 2004-10-25
[QUOTE=rupert]bump[/QUOTE]
 Well, what does "ioctl: LOOP_SET_FD: Das Gerät oder die Ressource ist belegt" mean? :D

---

### Post by tambooki on 2004-10-25
Well, this may be a little late since you're already on the cryptoloop path, but cryptoloop is being phased out in favor of dm-crypt, I believe. The article at [http://kerneltrap.org/node/view/2433](http://kerneltrap.org/node/view/2433) discusses why you would want to use dm-crypt instead, and [http://www.saout.de/misc/dm-crypt/](http://www.saout.de/misc/dm-crypt/) is information on how to set it up. Since it is newer, it might be a little harder to get running than cryptoloop, which is more established. I just though I'd mention it, since it seems to be a more secure and cleaner implementation. My ubuntu system seems to already have all the kernel stuff necessary, so I think you'd just need the userspace tools, which I think is in the "cryptsetup" apt package.

---

### Post by rupert on 2004-10-26
thx, im investigating it:
seems they all are not very safe:

[http://seclists.org/lists/linux-kernel/2004/Feb/4836.html](http://seclists.org/lists/linux-kernel/2004/Feb/4836.html)

---


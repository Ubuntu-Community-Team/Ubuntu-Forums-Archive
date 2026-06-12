---
title: "[Question] Increase home partition from root partition"
date: 2010-03-05
forum: General Help
---

### Post by Chromagnum on 2010-03-05
Hello. Recently I'm thinking about increasing home partition. Mainly because root partition is too big (or I could be wrong, though. Still need more explanation on this). To understand better I enclosed the screenshot from Gparted.

[IMG]http://i46.tinypic.com/2a98vbc.png[/IMG]

What I would like to do is: move some unused space from root (sda2) and merge it with home (sda3). Let's say about 5 or 6 GB. Can it be done without destroying anything? I mean, filesystem, data, etc. Perhaps someone could explain to me, what should and shouldn't be done or could and couldn't be done. 

Thank you in advance,
Chromagnum.

---

### Post by ibuclaw on 2010-03-05
Firstly, I think you should do a good deal of spring cleaning. ;)

Secondly, you can resize the partitions with the LiveCD (this ensures that the filesystems are unmounted). But as you are using the ext4 filesystem, I do not recommend this, due to known issues in the past with resizing them - memory corruption, loss of data, unmountable filesystem.

If you do go ahead and resize them, be prepared to wait a good 15 hours for it to complete though.

Regards
Iain

---

### Post by Chromagnum on 2010-03-05
> **ibuclaw said:**
> Firstly, I think you should do a good deal of spring cleaning. ;)

Secondly, you can resize the partitions with the LiveCD (this ensures that the filesystems are unmounted). But as you are using the ext4 filesystem, I do not recommend this, due to known issues in the past with resizing them - memory corruption, loss of data, unmountable filesystem.

If you do go ahead and resize them, be prepared to wait a good 15 hours for it to complete though.

Regards
Iain

Do you mean temporary files, cache, packages, etc? Oh, it is clean. I always clean that up nicely done. Used space from home is mainly my datas: music, movie, some stuff, etc. Since my external Hdd already running out of space, so I can't back it up (for now). Next month I will purchase new Hdd external. 

So basicly what you are saying it is a big risk to perform such a thing on ext4? I wouldn't do it then. On the related topic: you can see the root partition used about 3.9 GB. I've set it up from installation about 15 GB. My question is: is it too big? I'm still confused about how much space spend on root partition.

Thanks Iain.

---

### Post by ibuclaw on 2010-03-05
> **Chromagnum said:**
> Do you mean temporary files, cache, packages, etc? Oh, it is clean. I always clean that up nicely done. Used space from home is mainly my datas: music, movie, some stuff, etc. Since my external Hdd already running out of space, so I can't back it up (for now). Next month I will purchase new Hdd external. 

So basicly what you are saying it is a big risk to perform such a thing on ext4? I wouldn't do it then. On the related topic: you can see the root partition used about 3.9 GB. I've set it up from installation about 15 GB. My question is: is it too big? I'm still confused about how much space spend on root partition.

Thanks Iain.

10-15GB is usually just fine for a root partition. As applications tend to be small (with the exception of software with huge graphics packages - ie: games), and people don't install that many of them.


The risk may not be evident today, but I don't think it is worth trying it to find out...

(edit): [http://gparted-forum.surf4.info/viewtopic.php?id=13777](http://gparted-forum.surf4.info/viewtopic.php?id=13777)

---

### Post by Chromagnum on 2010-03-05
> **ibuclaw said:**
> 10-15GB is usually just fine for a root partition. As applications tend to be small (with the exception of software with huge graphics packages - ie: games), and people don't install that many of them.


The risk may not be evident today, but I don't think it is worth trying it to find out...

(edit): [http://gparted-forum.surf4.info/viewtopic.php?id=13777](http://gparted-forum.surf4.info/viewtopic.php?id=13777)

Ok then — confirmed. I won't do it. I should just wait next month for new external Hdd. But, I would like to find out more about ext4 and Gparted. Perhaps browsing through the whole forum for the related topics. Btw, the link you provided is great. Thanks!

I'm gonna close this thread now. Once again, thanks alot Iain. Really appreciated.  

Regards,
Chromagnum.

---


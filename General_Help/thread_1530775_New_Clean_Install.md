---
title: "New Clean Install"
date: 2010-07-14
forum: General Help
---

### Post by Quarkrad on 2010-07-14
I have made a clean install number of times.  At the point where you (I always do this) manually select the partition where you want Ubuntu to be installed there is a option where you want the Mount Point.  The options are /  /boot   /home   /tmp  /usr  etc. up to now I have always used  /  but I'm not sure effect choosing some of the options would be.

---

### Post by indytim on 2010-07-14
You need to define the "/".  All of the others provide optional storage (partitions) for the constituent parts of the ops.  For example, if you're using your /home as your document and media storage and you have a ton of that material, you may want to define a separate partition for /home also.  The rest of the options follow suit.

Also you can define other partitions and the associated mount point with the manual partition method.  As an example, I have a dedicated /boot partition (GRUB 1x), that is in sda5.  At the time of configuring a new install, I select the sda5 partition with the edit option.  Where you have the pulldown for the various options (/, /home etc.) in here I insert /media/GRUB.  Now the sda5 will be mounted in /media/GRUB on each bootup.

Hope this helps.

IndyTim / DataMan

---


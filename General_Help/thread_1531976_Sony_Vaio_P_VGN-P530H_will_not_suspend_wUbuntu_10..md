---
title: "Sony Vaio P VGN-P530H will not suspend w/Ubuntu 10.04"
date: 2010-07-15
forum: General Help
---

### Post by Jishenaz on 2010-07-15
Previously, my Vaio P (VGN-P530H) was able to suspend successfully in Ubuntu 9.04. Last December, I upgraded to Ubuntu 9.10 and suspend didn't work. Back then, I couldn't find any solution so I reinstalled 9.04.

Now with Ubuntu 10.04 released a few months ago, I was eager to upgrade again, since some of the software in 9.04 was old and the new version looked very nice, in my opinion. After upgrading to 10.04, suspend no longer worked. 

When I try to suspend, the screen goes black as it should, but the power led stays green instead of turning orange as it did in 9.04. I cannot wake to Vaio P in this state unless I do a hard boot.

The fact that suspend doesn't work on my Vaio P makes using it a huge inconvenience, since it overheats a lot if you don't put it to rest. And since I love the new 10.04, there's no way I'm going back to 9.04. Plus, everything else like brightness adjust keys work on 10.04, making suspend the only problem.

It would be wonderful if there was a way to make suspend work on VGN-P530H. It would make my Vaio P and Ubuntu a match made in heaven. Thanks.

---

### Post by ldrn on 2010-08-03
Hello;

I was able to get my Vaio P (slightly later model) to suspend with 10.04 with the following steps cribbed or adapted from elsewhere:

sudo apt-get uninstall vbetool
sudo apt-get install uswsusp

then replace /usr/sbin/pm-suspend with this:
```

#!/bin/sh
#remove wlan modules
for m in `lsmod | grep ath9k | awk '{print $1}'` ;
do
rmmod $m
done

s2ram --force

modprobe ath9k

```

... however, I ended up switching to Karmic anyway for other reasons. (Side note, the above will not work with Karmic.)

---

### Post by koymack on 2010-08-09
This worked for my VAIO SR35G running under LUCID... SUSPEND now is working... THANKS!!!

---


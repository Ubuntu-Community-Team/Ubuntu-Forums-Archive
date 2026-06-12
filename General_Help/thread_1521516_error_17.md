---
title: "error 17"
date: 2010-06-30
forum: General Help
---

### Post by ejames82 on 2010-06-30
it's been about 5 months since i installed a dual-boot of xp professional and jaunty.  the computer is a compaq presario sr1403wm with at least 1gb ram.  about 4 months ago i was unable to boot because i received a message:


GRUB Loading stage 1.5.

GRUB loading, please wait...
Error 17


overnight, the message was still there.  it wasn't going to boot.
i reinstalled jaunty and my dual boot was working again.  the windows xp partition was unhurt.  all the data was still there, unchanged.  we lost data in the ubuntu partition, but heard about "remastersys" and tried it.  i successfully make a remastersys disk.  i actually (naively) thought i'd never have this problem again.

about 2 months ago, once again, receiving the exact same error 17message as above.  
i booted ubuntu live cd and gparted called the ubuntu partition "unknown".  i did a little investigating, and tried "super grub disk", but being a newbie, i really didn't know how to use it.  i decided to try the remastersys disk.  data was lost again, but found out the remastersys disk works properly.  once again the xp partition and all the data was unhurt.  the hard drive is less than a year old, so the problem shouldn't be that.

during those first two error messages, i'm not sure whether or not my wife upgraded to karmic or lucid.  if she did, that may have contributed to the problem.

just last week, again, the same error message.  i used the remastersys disk again.
again today, error 17.  same message.  i checked gparted again, and just like before, the linux partition is "unknown"

i also did a little searching for the /boot/grub directory, hoping for some info.  i couldn't find /boot/grub.

any expertise in this matter would be most appreciated.

---


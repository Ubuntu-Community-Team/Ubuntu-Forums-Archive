---
title: "Ubuntu won't boot!"
date: 2010-03-20
forum: General Help
---

### Post by lorderico on 2010-03-20
Hello,

My Ubuntu 9.10 system (installed using wubi) won't boot and I don't know why.  The logo comes up, then it goes away and a solid white line appears in the left corner of the screen and it stops there.

However, ubuntu is able to boot into the recovery shell.

I have done hard drive tests and memory tests but they all come up clean.  The only info. I know is that when I press control-alt-f1 during bootup this flashes on the screen for a second:

> fsck from util-linux-ng 2.16
mountall: cancelled
init: ureadahead-other main process (962) terminated with error code 4
init: ureadahead-other main process (964) terminated with error code 4
general error in mounting file system
A maintenance shell...
control-D will terminate this shell and re-try

After that it goes to the white solid line and I can't do anything.  I have let it sit like that for about 5 minutes before shutting it off.

I am not really sure how to diagnose the cause of the problem or fix it.  Any help would be greatly appreciated.

Thanks,
Eric


Could it have anything to do with the fact that running startx in the recovery mode says: "no screens available"?  Is that normal?

---


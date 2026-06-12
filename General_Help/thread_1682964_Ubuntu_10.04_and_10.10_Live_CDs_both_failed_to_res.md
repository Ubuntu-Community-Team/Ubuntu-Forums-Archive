---
title: "Ubuntu 10.04 and 10.10 Live CDs both failed to resize my partition!"
date: 2011-02-06
forum: General Help
---

### Post by s3a on 2011-02-06
I tried multiple times and they both failed! Why? What could I do to get past this issue?

If more information is needed, please ask.

Any help would be greatly appreciated!
Thanks in advance!

---

### Post by 3177 on 2011-02-06
did you try Gparted?

---

### Post by TeoBigusGeekus on 2011-02-06
What steps have you taken?
Give us a screenshot from gparted when run from a live cd.

---

### Post by s3a on 2011-02-06
I used Gparted unallocate 500 MB from the largest (/home) partition and give it to the root partition.

Here are the gparted_details.htm (zipped) file with the errors and a screenshot.

---

### Post by s3a on 2011-02-09
Bump

---

### Post by 3177 on 2011-02-09
Sorry, but I can't think of what could be causing this. Worst comes to worst, to could backup your stuff and re-install. Again sorry I couldn't be more help.

---

### Post by Mark Phelps on 2011-02-09
Can't tell from the screenshot, but a limitation of using Ubuntu LiveCDs is that they mount some Linux partitions by default, especially, the swap partition.

Thus, let's say you're using a large Extended partition and the swap partition is inside that.  Since that is mounted, GParted won't let you do anything to the containing Extended partition.

Check to ensure that NONE of the partitions are being mounted.

Other than that, don't know what else to recommend.

---

### Post by s3a on 2011-02-09
I have a few GBs of space left. I did unmount swap as I always do.

1) Is there a certain percentage or something of free space I need for resize operations?
2) Will upgrading from ext3 to ext4 give me a reasonable boost in chance of performing this successfully? (I'm planning to upgrade anyway - and by upgrade I mean convert the filesystem not reinstall from scratch).

Edit: Reinstalling is not an option because this is my school laptop and I consider it as important as others would consider a server.

---

### Post by s3a on 2011-02-12
I just tried on a Ubuntu 9.10 CD and it failed again. To be more precise, it failed at "read 65536 sectors using a blocksize of 32768 sectors" as shown in the screenshot.

P.S. The resize I was attempting was a slightly different one but I don't think that that matters much.

---

### Post by clhsharky on 2011-02-12
s3a

Try Gparted Live latest
[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

Much newer with bug fixes than on Ubuntu cd.
I prefer Gparted Live, it has always come through for me when Ubuntu cd hasn't. 


Sharky

---


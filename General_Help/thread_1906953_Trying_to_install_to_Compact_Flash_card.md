---
title: "Trying to install to Compact Flash card"
date: 2012-01-09
forum: General Help
---

### Post by hglez86 on 2012-01-09
Hi, I'm trying to do an install onto a CF card. I am using an old pc with 512 ram (which is its maximum) and 1.2 celeron. I have a new 4 GB aData Cf card which I connect to a CF to IDE 2.5 adapter, then the 2.5 to 3.5 ide adapter. I am having trouble when it gets to the partitioning where 11.10 freezes and 10.04 says it has problems with the size of the partitions. 

I have been reading and found that the partition size for those wont work, but someone managed to install 8.04 unto one, what they did was install without swap space. I tried with 10.04 without swap space but it did not work, so now i'm downloading 8.04 to try it out on that one. 

Hope it works. 

X_x

---

### Post by CharlesA on 2012-01-10
Moved to it's own thread.

Original thread can be found [here]("http://ubuntuforums.org/showthread.php?t=1402779").

---

### Post by efflandt on 2012-01-10
Generally 8 GB is recommended as a minimum for Ubuntu.  I have done a regular installation of an earlier Ubuntu version (maybe 9 something) without swap on 4 GB USB stick, but there was not much room left.

Just as an example 4 GB flash is about 3.7 GB formatted.  For a 16 GB SD card that I use to boot 64-bit 11.10 on a tablet PC, **df -B MB** shows 4190MB being used with just drivers and a few programs added.

---

### Post by C.S.Cameron on 2012-01-10
A Live, persistent install should work fine, I use this made with Unetbootin on my EEE PC. This takes less than 750MB leaving over 3GB for persistence.

Chances are that an older computer's BIOS will not handle a CF card/reader anyway.

---


---
title: "errors=remount-ro"
date: 2010-09-17
forum: General Help
---

### Post by andres-bracho on 2010-09-17
Hi,

I was playing with "sudo gedit /etc/fstab" on my Acer Aspire One ZG5 with Ubuntu NBR 10.04 only (100% windows free) and found this sentence in my / partition... "errors=remount-ro"

My computer seems to work perfectly fine. After many days of regular work and restarts the message is still there.

What it means? Why is it there? How can I fix it?

It's not a big since in 23 days I'm going to reformat, but I'm curious...  ; )

Thanks in advance,
Andrés.-

---

### Post by e79 on 2010-09-17
"errors=remount-ro" means that it will remount the partitions  as read-only when errors occur on this partition, nothing to be worried about, this is normal.
 
 
Taken from : [http://ubuntuforums.org/showthread.php?t=315850](http://ubuntuforums.org/showthread.php?t=315850)
 
Hope this helps

---

### Post by solar george on 2010-09-17
That means "If an error is encountered remount the filesystem read-only" this is to help prevent fs errors ruining your install.

---

### Post by andres-bracho on 2010-09-18
Thank you

---


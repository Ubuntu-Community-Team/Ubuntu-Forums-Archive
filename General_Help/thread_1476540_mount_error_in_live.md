---
title: "mount error in live"
date: 2010-05-07
forum: General Help
---

### Post by basicbill on 2010-05-07
Hi,
I have been running a live version (the previous stable one) on a 16 gig stick.
Played nice for a couple of months but now when I try to access the native ntfs file system, I get the following error message....

[I]Error mounting: mount exited with exit code 21: mount: according to
mtab, /dev/sda1 is already mounted on /media/C218FB9D18FB8F23[/I]

I think it might be related to a cold shutdown...that is a shutdown using the power switch and not the ubuntu shutdown routine.

Thoughts?

---

### Post by WorMzy on 2010-05-07
Is it already mounted there, or is this message completely erroneous?

Also, can you post the contents of /etc/mtab and /etc/fstab please.

---

### Post by basicbill on 2010-05-08
I couldn't even see etc/mtab!
But I checked in /media and I saw 6 instances of my cd drive .... there was a heavily protected cd in it.

I removed the cd, rebooted and all is well.

hmmmm...

anyway, thanks for the assist.

---

### Post by WorMzy on 2010-05-09
I'm glad you figured that out, I wouldn't have thought to check that!

Mark your thread as solved if you've fixed it. :)

(Thread tools -> Mark as solved)

---


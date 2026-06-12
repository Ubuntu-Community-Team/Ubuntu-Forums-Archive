---
title: "Ubuntu 8.04 won't mount my USB drive."
date: 2009-11-30
forum: General Help
---

### Post by tpearson1 on 2009-11-30
I'm using 8.04 and it always gives me this error when I plug in my flash drive to any usb port: 

"CANNOT MOUNT VOLUME Invalid mount option when attempting to mount the volume 'KINGSTON'."

I've tried mounting via the computer menu screen. I've been told to try and unmount first but I do not have that option.


Thanks for you help.

---

### Post by srfito on 2009-11-30
I have the same problem in Ubuntu 9.04. I know why this happens in my case, but don't know how to solve it. Maybe the answer to my question is also valid for the original post.

My problem is that I changed the mount options using right-click on my USB icon while it was mounted. I made a mistake, so when I try to mount it again, it gives this error. The problem is that I don't know how to change the option again. I even went to /etc/fstab and there's nothing there (only the cd-rom mount options). Can anybody help?

Thanks very much.

---

### Post by emigrant on 2009-11-30
plz post output:

sudo fdisk -l

and

gedit /etc/fstab

---


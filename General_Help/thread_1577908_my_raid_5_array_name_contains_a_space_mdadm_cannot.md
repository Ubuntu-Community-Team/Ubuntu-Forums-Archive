---
title: "my raid 5 array name contains a space mdadm cannot deal with it"
date: 2010-09-19
forum: General Help
---

### Post by glendo on 2010-09-19
My raid 5 array name contains a space (media storage) mdadm cannot deal with it. How can I either change the name of the array or give mdadm some other way to ID the array. On boot I get a message saying disk for /dev/media is not ready. I skip that and computer boots normally but I have to start the array and mount the partition manually. I have searched the web for an answer to no avail.
 
 
Ok I've got it.  I just removed all reference to the array name from mdadm.  Array now starts automatically.

---


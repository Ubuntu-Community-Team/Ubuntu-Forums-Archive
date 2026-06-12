---
title: "Accessing remote hard drives?"
date: 2009-11-11
forum: General Help
---

### Post by Kennycl on 2009-11-11
Hi,

I am running Ubuntu 9.10 on both my work computer and my home computer. I was wondering if it was possible to access the data on the work machine remotely without setting up a full remote desktop display. Some kind of remote mount? Any advice appreciated!

Cheers,

Kenny

---

### Post by hwttdz on 2009-11-11
To fetch data - scp
to work remotely - ssh
to work remotely with x forwarding - ssh -x
to mount a remote drive - sshfs

The man pages on each should set you up.

---

### Post by Kennycl on 2009-11-11
Thanks for those! I'll investigate.

Kenny

---


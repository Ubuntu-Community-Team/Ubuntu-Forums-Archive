---
title: "Synaptic Package Manager doesn't opens...."
date: 2010-09-21
forum: General Help
---

### Post by navinbht13 on 2010-09-21
I have installed ubuntu in E drive. I have a problem in Synaptic Package Manager .When I open Synaptic Package Manager the message comes like below.


[U]E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.[/U]

What should I do now please??????
Thanks

---

### Post by yetiman64 on 2010-09-21
It appears a package install has failed, with Synaptic closed copy and paste the code ```
sudo dpkg --configure -a
``` into a terminal, enter your password and when the terminal completes the task try to then reopen Synaptic.

If the terminal shows any errors copy and paste them back here for further review.

---


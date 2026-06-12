---
title: "I &quot;chmod a-x /&quot; - help me"
date: 2012-05-16
forum: General Help
---

### Post by rockballad on 2012-05-16
Hello,

I did a mistake: "sudo chmod a-x /". How can I fix my system now?

Look like I 'killed' myself :-(

Thanks for your help.

---

### Post by satish_j on 2012-05-17
> **rockballad said:**
> 
I did a mistake: "sudo chmod a-x /". How can I fix my system now?


From my observations,i can tell you there is little possibility to fix it.
If you have a dual boot OS,boot into it and take back-up of the Linux partition,format it and then re-install the OS afresh
I remember committing this same mistake some time back,searched a lot and even got it fixed to some extent,but not fully.
Even if you get some advices,it will not be a full-proof solution as there may be other issues which will be seen in due course of use.
Iam waiting for other inputs on this thread.

---

### Post by 7xs on 2012-05-17
If you haven't rebooted yet, just do a chmod a+x /

If you rebooted and your sytem hangs, you need to use the install disk to rescue your system. A startup, choose to boot from disk and choose the rescue option. Mount your old root system (/) and correct the permissions. Reboot.

---

### Post by rockballad on 2012-05-17
Thank you, it got fixed! You saved me a lot of work. Thanks so much!

---


---
title: "Virtualbox shared folder problem"
date: 2010-10-06
forum: General Help
---

### Post by ykubota on 2010-10-06
I am using Ubuntu 10.04 with virtualbox 3.2.8 with Windows 7 host.  The shared folder option was working until yesterday, but when I did updates of Ubuntu, it stopped working.  Fortunately, Virtualbox allows me to go back to older state of my Ubuntu, so I used it to go back to pre-update configuration where I can use the shared folders, but do anyone have similar experiences?  How did you solve the problem?  Binary search for which update is breaking the system?  Thanks,

---

### Post by soldier1st on 2010-10-07
i had a similar issue but i fixed it by removing the shared folder and enter it again and have the OS detect it again.

---

### Post by ykubota on 2010-10-10
I have figured out that as long as I don't use the update: linux-image-2.6.32.25-generic (New Install), virtualbox file share keeps working.

---

### Post by coldraven on 2010-10-10
>  I have figured out that as long as I don't use the update:  linux-image-2.6.32.25-generic (New Install), virtualbox file share keeps  working.
The same kernel broke my Suspend and wi-fi, I posted earlier today about that.
It should have been tested a bit more maybe!

---

### Post by ykubota on 2011-01-06
> **soldier1st said:**
> i had a similar issue but i fixed it by removing the shared folder and enter it again and have the OS detect it again.

Thank you for the idea.  I removed the shared folders but that alone did not seem to fix the problem.  Somehow, however, when I updated VBox version, as well as Guest Additions, it fixed itself.

Thanks,

---


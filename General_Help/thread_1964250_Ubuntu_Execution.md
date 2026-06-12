---
title: "Ubuntu Execution"
date: 2012-04-23
forum: General Help
---

### Post by ashkot on 2012-04-23
Hi all,
I installed Ubuntu on my HDD such that my PC is now dual boot. Although, now i need to run Ubuntu from within Windows and also call some web pages running on Apache on Ubuntu.

Can this be done? Any ideas in this regards will be much appreciated.

Thanks,
Ashwin

---

### Post by newbie-user on 2012-04-23
Yeah, install Ubuntu using wubi inside of Windows. I believe the desktop install cd comes with wubi.

---

### Post by papibe on 2012-04-23
Hi ashkot. Welcome to the forums!

I'm afraid that won't work on a dual boot system. When you are running Windows, your dual-boot-Ubuntu system can't be run at the same time (thus Apache won't be available).

A solution would be to install a VirtualBox in Windows and install Ubuntu as a guest OS. That way both can be run at the same time.

I hope that help, and tell us how it goes.
Regards.

---

### Post by ashkot on 2012-04-23
Yes, i can try virtual box, just that the issue now is I have a version already installed and now i have to have another one. That will take some space but also I will have to maintain two separate versions.

Ashwin

---


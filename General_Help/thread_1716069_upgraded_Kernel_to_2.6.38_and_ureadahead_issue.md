---
title: "upgraded Kernel to 2.6.38 and ureadahead issue"
date: 2011-03-27
forum: General Help
---

### Post by Viperman0986 on 2011-03-27
Hello,

I am running Ubuntu Desktop 10.04LTS with no dual-boot and I installed the latest kernel using instructions from this website: [http://www.ramoonus.nl/2011/03/linux-kernel-2-6-38-installation-guide-for-ubuntu-linux/](http://www.ramoonus.nl/2011/03/linux-kernel-2-6-38-installation-guide-for-ubuntu-linux/)

Everything went smooth but for some reason I am seeing a longer boot time than before and now I receive an "init: ureadahead main process (198) terminated with status 5" error message on boot before it gets to the desktop.

I did some research and found this site explaining ureadahead and what it does but it doesnt mention anything about status 5 errors only status 4. [http://ubuntuguide.net/howto-fix-ureadahead-problem-after-upgrading-to-ubuntu-10-04](http://ubuntuguide.net/howto-fix-ureadahead-problem-after-upgrading-to-ubuntu-10-04)

I'm pretty sure this status 5 error is why my boot has slowed down so does anyone have any ideas on how to resolve it?

any help or advice is appreciated

Thanks in advance!

---

### Post by Dark_Stang on 2011-03-27
Don't worry about it. Also, UReadAhead doesn't affect boot speed, if anything it would slow it down slightly as it tries to load extra files on startup that you may need later.

---

### Post by Viperman0986 on 2011-03-28
> **Dark_Stang said:**
> Don't worry about it. Also, UReadAhead doesn't affect boot speed, if anything it would slow it down slightly as it tries to load extra files on startup that you may need later.

Ah ok, thanks for the explanation, I was just worried cause it was a status 5 error.  Ill just leave it be.

---

### Post by Dark_Stang on 2011-03-28
> **Viperman0986 said:**
> Ah ok, thanks for the explanation, I was just worried cause it was a status 5 error.  Ill just leave it be.

It happens when you compile your own kernel or install a custom kernel.

---

### Post by Viperman0986 on 2011-03-29
I understand, I will mark this as solved now!:)

---


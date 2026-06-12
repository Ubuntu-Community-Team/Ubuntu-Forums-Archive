---
title: "why do i have to many things in the boot menu?"
date: 2010-02-02
forum: General Help
---

### Post by aviramof on 2010-02-02
i have ubuntu 8.10 kernel 2.6.27-16-generic then recovery mode then ubuntu 8.10 kernel 2.6.27-7-generic
then recovery mode then memtestx86 and windows 7 loader i don't mind recovery mode and memtest but what is ubuntu 8.10 kernel 2.6.27-7-generic and what do i do with that?


p.s what is the difftent between ubuntu 8.10 cd and 10.4 TLS dvd i downloaded from here [http://cdimage.ubuntu.com/dvd/current/](http://cdimage.ubuntu.com/dvd/current/)

thanks in advance.

---

### Post by &#27832;&#12363;&#12373;&#12428;&#12383;&#39770;&#12398;&#20154;&#12399;&#29483;&#12434;&#33296; on 2010-02-02
2.6.27-7 is the the older kernel. It is not used anymore.

---

### Post by aviramof on 2010-02-02
i see can i remove it somehow?like limit the amount of kernetl to 1 in startupmanager (sudo apt-get install startupmanager) and it want hide my windows 7 loader?

---

### Post by &#27832;&#12363;&#12373;&#12428;&#12383;&#39770;&#12398;&#20154;&#12399;&#29483;&#12434;&#33296; on 2010-02-02
> **aviramof said:**
> i see can i remove it somehow?like limit the amount of kernetl to 1 in startupmanager (sudo apt-get install startupmanager) and it want hide my windows 7 loader?

Yes, but I would just leave it alone.

---

### Post by houseworkshy on 2010-02-02
Actually it is a safety device; if you have problems with the new one you still have the option of going backwards.  I'd recommend keeping at least one of the old pair, generic and it's recovery mode, just in case. You can get rid of the old one's, you can even specify how many to keep so as the latest is added the oldest is automatically ditched.  So set kernel to 2.  Taking it down to 1 would be as unwise as removing system restore from windows.

[http://www.ubuntugeek.com/how-to-change-settings-for-the-bootloader-and-splash-screen-in-ubuntu.html](http://www.ubuntugeek.com/how-to-change-settings-for-the-bootloader-and-splash-screen-in-ubuntu.html)

---

### Post by aviramof on 2010-02-03
ok thanks i'll keep it there for now on at least.

---

### Post by houseworkshy on 2010-02-03
There are quite a few differences between 10.04lts and 8.10. The numbers are the year and month of release and the "lts" means long term support. An Ubuntu is released every six months but an lts only comes out every two years. It is not yet declared stable. It probably still has bugs as it is in the testing stage so if you know your stuff you can help get it ready if not it may be better to wait until it's official release date. The long term supports are maintained for three years, the current one is the 8.04lts. Even when it is released I'd leave it a few months as though it may be stable the manufacturers of proprietary drivers may not yet have caught up. Looking at the forums will give you the hint. Searching for posts about your video driver in particular is worth doing before making the jump. I put in 9.10 within a few days of it coming out and had no end of headaches until nvidia caught up. Easy as clockwork a month or two later when the hardware drivers and update manager ( in Administration ) sorted everything out.

---

### Post by aviramof on 2010-02-03
thanks for the info i think i would wait till april 29 to update to version 10 becase 9 version didn't worked so well for me.

---


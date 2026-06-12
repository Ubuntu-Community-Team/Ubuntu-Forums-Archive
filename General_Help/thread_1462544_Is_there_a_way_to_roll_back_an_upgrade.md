---
title: "Is there a way to roll back an upgrade?"
date: 2010-04-25
forum: General Help
---

### Post by Roasted on 2010-04-25
I had Ubuntu 9.04 on my mom's laptop. For some reason both 9.10 and 10.04 didn't work with the wireless, DESPITE it having Atheros wireless which "should work out of the box." Yeah okay. Not in this case.

She upgraded to 9.10 on accident. Bingo. No wireless.

Can I roll it back... somehow?

---

### Post by tica vun on 2010-04-25
Nope. Try upgrading to 10.04 instead.

---

### Post by Roasted on 2010-04-25
> **tica vun said:**
> Nope. Try upgrading to 10.04 instead.

> **Roasted said:**
> I had Ubuntu 9.04 on my mom's laptop. For some reason both 9.10 ***and 10.04*** didn't work with the wireless, DESPITE it having Atheros wireless which "should work out of the box." Yeah okay. Not in this case.
.

---

### Post by clhsharky on 2010-04-25
HI Roasted

I had many problems with .32 kernel, .33 is better but .34 even rc is way more wifi friendly. I dont know if your using OSS drivers or not but if you are try newer kernel.

Here what I had to do, install lucid 'no network connection' in stall 2.6.33 'network connected', then upgrade. The Ubuntu default kernel would work but I was getting dropped at least once a day. Only router reboot would get me on network, I had DNS troubles many sites were unavailable or slow or timed out. Kernel 2.6.34.rc5 has non of these problems plus better signal strength.

If you have to have proprietary drivers " NV/ATI " your stuck with .32 kernel.
Oh well thats my 2cents.

Sharky

---

### Post by Roasted on 2010-04-25
The problems I have are I can connect to wireless, but not with any form of security.

I don't understand how through two versions of Ubuntu one of the most common wireless cards out there managed to not get fixed. But I'll try the RC - maybe I'll have better luck...

---

### Post by conradin on 2010-04-26
On boot is there an option for the old kernel?
If the old kernel is still available, then you should be able to remove the new one. That is after all, the point of having the feature.

---

### Post by Roasted on 2010-04-26
I booted up to the .18 kernel and was able to get on wireless just fine. The .20 kernel was the one where wireless stopped working.

One problem: The trackpad didn't work.

.18 - Wireless, no trackpad.
.20 - No wireless, trackpad.

Come the **** on... ](*,)](*,)](*,)](*,)](*,)](*,)](*,)

EDIT - It's okay guys. I just tried 10.04 RC, and it too failed to work.

Happy thoughts. Happy thoughts. Happy thoughts.

---

### Post by conradin on 2010-04-27
I would try to fix the wifi. Here is Atheros's support page.
[http://www.atheros.com/news/linux.html](http://www.atheros.com/news/linux.html)
[http://sourceforge.net/projects/madwifi/](http://sourceforge.net/projects/madwifi/)

---


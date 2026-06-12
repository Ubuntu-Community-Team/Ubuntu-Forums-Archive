---
title: "Update stuck"
date: 2012-02-03
forum: General Help
---

### Post by JCM_Pico on 2012-02-03
hi there,

I am installing kubuntu for the first time on my pc and when running Software Updates (339 to be installed) it got stuck at 50% in "running dpkg". It has been there for at least 5 minutes and doesn't move... The load led of my pc is off... 

Is this normal, is it a bug, what is it? 

Thanks!

---

### Post by sikander3786 on 2012-02-03
You mean it got stuck while installing the packages and has already downloaded all of them? It would be really helpful if you could post the 5-6 lines of text from the Update window.

Just a hint, don't reboot your PC for now.

---

### Post by JCM_Pico on 2012-02-03
> **sikander3786 said:**
> You mean it got stuck while installing the packages and has already downloaded all of them? It would be really helpful if you could post the 5-6 lines of text from the Update window.

Just a hint, don't reboot your PC for now.


Uups! Your hint came to late! Already rebooted it... 

But, good news, problem solved! After rebooting everything was kind wacky but running ```
sudo dkpg --configure -a
``` solved the problems and kubuntu is now running smoothly.

Thank you anyway!

---

### Post by sikander3786 on 2012-02-03
> **JCM_Pico said:**
> Uups! Your hint came to late! Already rebooted it... 

But, good news, problem solved! After rebooting everything was kind wacky but running ```
sudo dkpg --configure -a
``` solved the problems and kubuntu is now running smoothly.

Thank you anyway!
Thankfully, it wasn't something serious. :)

Yeah, that's what we would have done but without rebooting the PC, I mean without taking the risk.

Anyway, Good Luck!

---

### Post by JCM_Pico on 2012-02-03
> **sikander3786 said:**
> Thankfully, it wasn't something serious. :)

Yeah, that's what we would have done but without rebooting the PC, I mean without taking the risk.

Anyway, Good Luck!

Risk is my middle name ;) and it was a fresh install with nothing on it.....

---


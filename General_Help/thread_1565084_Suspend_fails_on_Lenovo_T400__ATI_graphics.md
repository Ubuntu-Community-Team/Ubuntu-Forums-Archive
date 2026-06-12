---
title: "Suspend fails on Lenovo T400 / ATI graphics"
date: 2010-08-31
forum: General Help
---

### Post by riprowan on 2010-08-31
Suspend works about 50% of the time on my T400.  The other 50% of the time, the screen goes blank (light stays on), there is a blinking cursor in the top left, and the "moon" light blinks forever.

I've got the latest ATI (3470?) video driver installed.

I've seen a few posts about this but no clear solution.  Anyone here have this problem and (more importantly) been able to fix it? 

Help greatly appreciated.  TIA.

---

### Post by riprowan on 2010-09-02
** bump **

---

### Post by riprowan on 2010-09-04
Really?  Nobody else has this problem?

[*UPDATE*]

Updated my BIOS.  No improvement.  If anything it's worse.

---

### Post by efflandt on 2010-09-04
Are you using any non-default video driver?  My only ATI experience is with legacy chips (X1300 desktop and mobile) and I had to use **nomodeset** kernel boot parameter for suspend/hibernate to work on my older desktop and to eliminate boot video glitches on the laptop.  Otherwise by default 10.04 uses new kernel mode setting (KMS) for ATI, and **nomodeset** uses regular user space modules instead.

---

### Post by riprowan on 2010-09-05
I think you're onto something here.

Yes, I am using the proprietary ATI drivers.  Disabling them seems to resolve the sleep issue (after a VERY cursory test).  However, I can't leave them disabled, since doing so causes the computer to run VERY hot and battery life is about 30 mins.

HELP!?

---

### Post by riprowan on 2010-09-05
> **efflandt said:**
> Are you using any non-default video driver?  My only ATI experience is with legacy chips (X1300 desktop and mobile) and I had to use **nomodeset** kernel boot parameter for suspend/hibernate to work on my older desktop and to eliminate boot video glitches on the laptop.  Otherwise by default 10.04 uses new kernel mode setting (KMS) for ATI, and **nomodeset** uses regular user space modules instead.

OK - I added the nomodeset param, and it seems (on cursory test) to have resolved the sleep issue.  I will report back if this causes  the power consumption / heat problem to return, however.

---


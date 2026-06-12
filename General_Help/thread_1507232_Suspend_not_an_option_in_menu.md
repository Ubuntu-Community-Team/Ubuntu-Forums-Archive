---
title: "Suspend not an option in menu"
date: 2010-06-11
forum: General Help
---

### Post by sgardne on 2010-06-11
First, I apologize if this has already been covered. I searched the forums and google a bit but did not find quite this issue anywhere. If this has already been covered, please point me in the direction of information. 

So, I installed Ubu desktop 32b version on my desktop computer last night. It's got an AMD chipset with integrated graphics card. In the menu with the logout restart, shutdown, et cetera there is supposed to be a Suspend option, but it is not available. Is there anything I can do to make my computer suspend? Hibernate works as expected. 

Thanks in advance!

---

### Post by TeoBigusGeekus on 2010-06-11
Try
```
sudo pm-suspend
```
from terminal

---

### Post by sgardne on 2010-06-11
Sorry for the late reply. That command does nothing for me.

---

### Post by dcstar on 2010-06-12
> **sgardne said:**
> First, I apologize if this has already been covered. I searched the forums and google a bit but did not find quite this issue anywhere. If this has already been covered, please point me in the direction of information. 

So, I installed Ubu desktop 32b version on my desktop computer last night. It's got an AMD chipset with integrated graphics card. In the menu with the logout restart, shutdown, et cetera there is supposed to be a Suspend option, but it is not available. Is there anything I can do to make my computer suspend? Hibernate works as expected. 

Thanks in advance!

Do you have Suspend enabled in your BIOS?

---

### Post by sgardne on 2010-06-12
Thanks for reminding me to check the BIOS. Suspend was enabled, but it was in S1 mode. I put it in S3 mode and now it works as expected.

---


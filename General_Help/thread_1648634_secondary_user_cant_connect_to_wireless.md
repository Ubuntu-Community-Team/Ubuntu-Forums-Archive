---
title: "secondary user cant connect to wireless"
date: 2010-12-19
forum: General Help
---

### Post by Angelbrand on 2010-12-19
i have been reading through the linux guide as the bash tutorial said i should before learning bash. 
The Guide told me i shouldnt use the administrator account as my everyday account so i added a new user but the network manager doesnt show and i cannot connect to my wireless internet. I have approved the secondary account to access the net and everything but i cant figure this out.

---

### Post by spiky001 on 2010-12-19
Hi if you open network manager with right click then edit connections open wireless tab tick the box at bottom all users

---

### Post by QLee on 2010-12-19
> **Angelbrand said:**
> i have been reading through the linux guide as the bash tutorial said i should before learning bash. 
The Guide told me i shouldnt use the administrator account as my everyday account so i added a new user but the network manager doesnt show and i cannot connect to my wireless internet. I have approved the secondary account to access the net and everything but i cant figure this out.

One thing that might be worth checking:
Log in as the user with admin permissions.
Right click the Network Manager icon to edit connections and select the connection you want to use.
Make sure the box down at the bottom, Available to all users, is checked. Then log back in as non-admin user and see if you have access.

Edit:Ha, apparently we're thinking alike on this one spiky.

---

### Post by Angelbrand on 2010-12-19
thanks guys!!!

---


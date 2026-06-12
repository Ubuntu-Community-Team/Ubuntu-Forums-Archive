---
title: "can't get into evolution after adding new account"
date: 2012-04-21
forum: General Help
---

### Post by pennyminstrel on 2012-04-21
Hi,

I just added a second account in evolution, went to restart it and it's asking for the password for the new account. The trouble is that I can't type into the password box, nothing happens. The keyboard is working fine, ie I can type in other applications. Also, if I try to cancel or close the box nothing happens and the only way I can get it to go away is to use force quit, so now I can't get into evolution at all.

Any suggestions,
Many thanks
Penny

---

### Post by dino99 on 2012-04-21
maybe

 sudo dpkg-reconfigure evolution

or you have some borked settings inside .gconf/evolution

---

### Post by pennyminstrel on 2012-04-21
Thanks for your reply dino66. I tried the command you suggested with no result. I guess, yes I must have borked some settings unknowingly, but I have no idea what or how to put it right, so any more suggestions would be very gratefully accepted

---

### Post by pennyminstrel on 2012-04-21
I've now discovered that hiding behind the box asking me to enter the password for the new account was another one asking if I wanted to recover a message left unfinished when I last shut down. Once I got rid of that, I could get into my evolution settings and delete the new, dysfunctional account, so am at least now back to square one.

---

### Post by dcstar on 2012-04-21
> **pennyminstrel said:**
> I've now discovered that hiding behind the box asking me to enter the password for the new account was another one asking if I wanted to recover a message left unfinished when I last shut down. Once I got rid of that, I could get into my evolution settings and delete the new, dysfunctional account, so am at least now back to square one.

You can also start Evolution in offline mode so it doesn't try and connect which causes the password prompt:

```
evolution --offline
```

Just remember to go back into "Online" mode after you fix your issues.

---


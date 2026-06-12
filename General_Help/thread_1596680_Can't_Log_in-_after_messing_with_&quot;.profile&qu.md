---
title: "Can't Log in- after messing with &quot;.profile&quot;"
date: 2010-10-14
forum: General Help
---

### Post by Damascushead on 2010-10-14
Every time I try to log in from the log in screen, the screen goes black and then returns to the login screen. 
 
I'm not sure, but I think the cause is that I was messing around with my ".profile" as I am trying to learn shell scripting. After doing so I logged out and tried to log in to see the changes I had made. I then encountered the problem. 
 
I tried editing the .profile as another user to remove the portion that I had messed with, but I couldn't save it.
 
 
I am running 10.10, which has worked flawlessly for the last couple of days.
 
Any help would be greatly appreciated!
 
Thanks.:P

---

### Post by anglican on 2010-10-14
> **Damascushead said:**
> Every time I try to log in from the log in screen, the screen goes black and then returns to the login screen. 
 
I'm not sure, but I think the cause is that I was messing around with my ".profile" as I am trying to learn shell scripting. After doing so I logged out and tried to log in to see the changes I had made. I then encountered the problem. 
 
I tried editing the .profile as another user to remove the portion that I had messed with, but I couldn't save it.
 
 
I am running 10.10, which has worked flawlessly for the last couple of days.
 
Any help would be greatly appreciated!
 
Thanks.:PAssuming your "other" user can't sudo edit your .profile, try a console login by pressing [CTRL]-[ALT]-[F1] together. If you can't get a console in that way, you may need to boot into "recovery mode". If none of these work then booting from a live CD is the final thing to do.

H

---

### Post by endotherm on 2010-10-14
I'd just try to rename your bad .profile. it will be regened from defaults on subsequent reboot.
you can do that with another user, a live CD or recovery mode.

---

### Post by Damascushead on 2010-10-14
Thank you both of you. I was able to boot in recovery mode and then get in on the root user command prompt. pulled up and edited the .profile with emacs and now I can log in. Thanks!

---


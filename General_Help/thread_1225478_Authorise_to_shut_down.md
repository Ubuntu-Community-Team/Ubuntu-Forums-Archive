---
title: "Authorise to shut down ?"
date: 2009-07-28
forum: General Help
---

### Post by wimmelis on 2009-07-28
Dear all, 

Since a few days, my Ubuntu 9.04 (64-bit) asks me to authorise when I choose to shut down. It mentions that "System policy prevents stopping the system when other users are logged in", which I can understand as a preventive measure. Though ... there is only one user on that machine ?? So, who else could be logged on then ?
How do I overcome this problem ?


Thanks, 

WM

---

### Post by philcamlin on 2009-07-28
are you logged in as root somewhere? 

it: terminal etc

---

### Post by wimmelis on 2009-07-30
Hi,


Well, I always need some root privileges for something during my working session, but generally, I shut down my programs before I choose for shut-down, so they should all be logged out unless that does not happen when you close the application ??


Regards, 

WM

---

### Post by motoperpetuo on 2009-08-12
i started getting this message when shutting down recently, right around the time one of my computers was pretty obviously compromised by an attacker. could this be an indication of a root kit or someone else logging on to my computer surreptitiously? how would i know? how can you bring up a list of open sessions on your computer?

---

### Post by dcstar on 2009-08-12
> **motoperpetuo said:**
> i started getting this message when shutting down recently, right around the time one of my computers was pretty obviously compromised by an attacker. could this be an indication of a root kit or someone else logging on to my computer surreptitiously? how would i know? how can you bring up a list of open sessions on your computer?

```
who
```

---

### Post by motoperpetuo on 2009-08-21
> **dcstar said:**
> ```
who
```

would 'who' ever actually show you that some unwanted person is accessing your system remotely?

---

### Post by zong1 on 2009-09-03
I think the point is: How the **** does one disable this stupid idea.  I own the computer not the computer owns me, or are we all too stupid to make the decision about when the turn the PC off ourselves.

Otherwse, do I have a write a special script called shutdown & put it in the laucher that contains:

#!/bin/sh
su - halt

With an entry in the passwd file that does this with out a passwd in shadow:
```

halt:x:0:1002::/var/tmp:/sbin/halt  
```

I upgraded to 9.04 for other reasons than being told: [I]Are you sure you want to do this, Dave?
[/I]

/edit: Too late already done it and it works much better.  //yeah whatever... ^^

---


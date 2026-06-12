---
title: "Log in problems"
date: 2009-07-01
forum: General Help
---

### Post by ntrc on 2009-07-01
Hi, I am a novice Linux user.

Please advise me on the following problem

While attempting to get a permission to place files in /usr directory, I changed my user directory from home to root and added another user with limited privileges.  I did not change password for the first user and dis not set up any password for the second user.  After that, I was not able to log-in after restart.   At first, there are error messages indicating that Desktop directory cannot be created. Next, I am asked to enter user name and password.  It would not accept my user name and password.

In order to solve a problem, I tried several things
Changed kernel by adding "single".   
Changed password through "recovery mode"

My password is accepted in the recovery mode as "root password" and I am able to get to the bash prompt.
By typing cat / etc / passwd I can see my user name and that root (rather than home) is the user directory.

Perhaps, the problem is that user directory has to be changed back to "home"

How do I do it?

---

### Post by sisco311 on 2009-07-01
```
usermod -d /home/username username
```

---

### Post by ntrc on 2009-07-01
O:)> **sisco311 said:**
> ```
usermod -d /home/username username
```
Thank you very much!

It worked.

---


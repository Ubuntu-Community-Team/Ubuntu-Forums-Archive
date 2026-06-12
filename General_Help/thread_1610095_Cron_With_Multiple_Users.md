---
title: "Cron With Multiple Users?"
date: 2010-10-31
forum: General Help
---

### Post by csharpplus on 2010-10-31
I am a newbie, so bear with me if the answer to this is too obvious.

Let's suppose that a machine has three users:

(1) david
(2) dan
(3) joel

The computer now restarts and during the log-in process, I choose to login into dan's account.

At this point, when I am logged in into dan's account, will Ubuntu run the crontab jobs that belong to david / joel?


Thanks for any help.

---

### Post by Dave_L on 2010-10-31
cron runs independently of who is logged in. Even if no one is logged in, the crontab jobs will run.

---

### Post by csharpplus on 2010-10-31
Is this true for all users?

---

### Post by DaithiF on 2010-10-31
> **csharpplus said:**
> Is this true for all users?
Yes, or at least all users with crontabs

---

### Post by csharpplus on 2010-10-31
Great, thanks!

---


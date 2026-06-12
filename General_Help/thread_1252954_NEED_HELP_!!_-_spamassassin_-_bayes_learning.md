---
title: "NEED HELP !! - spamassassin - bayes learning"
date: 2009-08-29
forum: General Help
---

### Post by cbear on 2009-08-29
I would like to run a nightly script to learn spam from a single folder and apply the "learning" to all users on the system.  I read a ton of info and I have configured the following flags in /etc/spamassassin/local.cf:

```
use_bayes 1
bayes_auto_learn 1
```

Since this is spammassassin 3.x, I don't need the use_auto_whitelist flag based on what I have reseached.

My nightly script (learn.spam) learns from a folder in my user directory called "newspam".  This is the script:

```
sa-learn --mbox --spam /home/tbegehr/mail/newspam
```

I have crontab set to run the job nightly at 4:10am with the following line:

```
10 4 * * * root /home/backups/learn.spam
```

** MY QUESTION **
Q: do I need to run this job as "root" or "tbegehr" ?  Does it matter ?  I want the spam learning to apply to all users, not just tbegehr.  If I run as "root" does that only apply to user=root or ALL USERS ?

---


---
title: "/etc/crontab busted? Upstart dilemmna?"
date: 2010-01-06
forum: General Help
---

### Post by trinaryouroboros on 2010-01-06
Forgive my ignorance. 

I was used to being able to add things to /etc/crontab without worrying (uhm, pretty much for over a decade...hence the lack of experience), but either something broke it, or something's not running properly here.

If I add the same business to root's crontab, it works fine, but the /etc/crontab file is clearly not running.  I believe cron-apt is running, because we still get security updates automatically.

I have a sneaking suspicion, however, that Likewise Open 5 (current product release) is interfering with the process that governs /etc/crontab, or something else is running before that process in Upstart, causing that process for crontab to fail.

We're using ubuntu server 9.10 amd64 in this case, freshly installed as of a couple of months ago.

Any help is highly appreciated, I've dug around with Upstart, and generally the changes that have occurred to Ubuntu since a couple of generations ago, and I'm completely lost.

:confused:

---

### Post by falconindy on 2010-01-06
/etc/crontab is for settings applicable to cron. Jobs should be entered in your own crontab, via 'crontab -e'.

---

### Post by Prometheus78 on 2010-01-07
Wow .. thank you .. that is so helpful. In any case .. the main system crontab ... that is suppose to work .. and run cron jobs .. doesn't.


-- yes I registered just so I could tell you that

---

### Post by trinaryouroboros on 2010-01-07
Okay, so just to elaborate real quick, since I installed Karmic server edition, the /etc/crontab has been working Fine, and actually Running Jobs.  Just recently, it Stopped doing this, and I'm looking for a method of troubleshooting this specific problem.  Does that make more sense now?

---

### Post by trinaryouroboros on 2010-01-07
Thinking about Canonical support for this stuff anyway, so much has changed since Hoary Hedgehog, I can barely stay on top of it anymore.

---

### Post by trinaryouroboros on 2010-01-23
My only guess is that it was something with Logzilla, unfortunately even in my professional opinion I can't gauge what did the trick - but apparently the /etc/crontab has begun working again, either on it's own, or because Google Code's version of Logzilla /syslog-ng began to run with positive results.

For the record, /etc/crontab still works today.  You can feel free to add things to Ubuntu on /etc/crontab without issue.

---


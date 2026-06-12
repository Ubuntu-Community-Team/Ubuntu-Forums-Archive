---
title: "Anacron sending email?"
date: 2009-07-07
forum: General Help
---

### Post by newlinux on 2009-07-07
I recently installed a configured postfix on one of my servers. The next day my regular local user account had email  about a job in cron.daily from my root account, I assume sent by anacron after it ran the job. I'm curious as to why this email went to my local user account. I thought by default anacron sent emails to the user running the job, which would be root. I have no "MAILTO" set in my /etc/cron.d/anacron  or /etc/anacrontab tabs. I'm just curious as to what I am not getting... Why did it decide to send the email to my local user account? Is this the default? 

Thanks for any information. I know mostly the basics around cron and anacron.

---

### Post by newlinux on 2009-07-07
Is this is due to /etc/aliases - which points root to my user. Does that sound correct?

---


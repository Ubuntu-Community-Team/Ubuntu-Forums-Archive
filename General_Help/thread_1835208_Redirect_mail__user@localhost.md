---
title: "Redirect mail  user@localhost"
date: 2011-08-29
forum: General Help
---

### Post by bibble235 on 2011-08-29
Hi,

I want to redirect my mail on the server to an account of my choosing. Looking in the mail it appears to be coming from cron. 

I have a virtual host mail server on the box with postfix/courier running.

I am sure this should be easy and do want a permenant solution. Converting using a script each time would be a pain.

Thanks all.
Iain

---

### Post by sisco311 on 2011-08-29
Use the MAILTO variable in your crontab file.

---

### Post by dcstar on 2011-08-29
> **bibble235 said:**
> Hi,

I want to redirect my mail on the server to an account of my choosing. Looking in the mail it appears to be coming from cron. 

I have a virtual host mail server on the box with postfix/courier running.

I am sure this should be easy and do want a permenant solution. Converting using a script each time would be a pain.

Thanks all.
Iain

Edit the /etc/aliases file and then run newaliases.

---


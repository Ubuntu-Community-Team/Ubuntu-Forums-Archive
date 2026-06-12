---
title: "Mutt Problem Receiving Mail"
date: 2012-04-05
forum: General Help
---

### Post by cssutto on 2012-04-05
Well, not really mutt.

I am setting up a new machine, with the usual problems.

Mutt can send mail.

Fetchmail does its thing as evidenced by syslog.

However, this is where receiving mail stops.

It never makes it to procmail.

None of the logs shows where it stops.

Ubuntu 10.4...mutt, msmtp, fetchmail, procmail.

Can any one tell me how to track the progress so I can tell where it stops?

---

### Post by andrew.46 on 2012-04-06
Can you post your ~/.fetchmailrc and ~/.procmailrc? Without username and passwords of course :).

---

### Post by cssutto on 2012-04-06
> **andrew.46 said:**
> Can you post your ~/.fetchmailrc and ~/.procmailrc? Without username and passwords of course :).

I have run mutt since 2007.

I have looked at both 100 times in the past few days but when I copied fetchmailrc and looked at removing passwords, user name, etc., I found that I was using the user name from the old machine.

So I fixed it.

Thanks for waking me up.

---


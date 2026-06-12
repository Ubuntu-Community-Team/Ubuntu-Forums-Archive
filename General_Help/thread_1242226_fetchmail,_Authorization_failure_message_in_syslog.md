---
title: "fetchmail, Authorization failure message in syslog"
date: 2009-08-16
forum: General Help
---

### Post by AlexBooton on 2009-08-16
Hi,

I'm using fetchmail to download mail into users' mailboxes via postfix.

Every message that comes in results in an error message in syslog.

   Authorization failure on <user>@<my domain>
   fetchmail[5074]: Query status=3 (AUTHFAIL) 

Even with this error message, the mail is getting in!?

I'm just nervous about the error and would like to clean it up.

Thanks for your help.

---

### Post by andrew.46 on 2009-08-18
Hi Alex,

> **AlexBooton said:**
> 

```
   Authorization failure on <user>@<my domain>
   fetchmail[5074]: Query status=3 (AUTHFAIL) 
```



Could you post your .fetchmailrc, or the fetchmail string you are using?

Andrew

---

### Post by AlexBooton on 2009-08-18
Hi Andrew,

Thanks for your help.  

This problem is troubling even though it doesn't seem to interfere with fetchmail actually downloading the mail.


Here's my /etc/fetchmailrc.  I've obscured private info.  

# set polling interval 900 seconds = 15 minutes
set daemon 200
set postmaster "ed"
set bouncemail
set no spambounce
set syslog
set properties ""

poll pop.<mydomain>
        timeout 30
        proto pop3
        interval 3

        user "ed@<mydomain>"
        pass "<my password>"
        is ed keep

        user "anna@<mydomain>"
        pass "<anna's p/w>"
        is anna keep

# This continues for several more users.

Thanks again.

---

### Post by andrew.46 on 2009-08-19
Hi AlexBooton,

My apologies but I have had a long look at fetchmail + multidrop, an aspect of fetchmail usage I have not considered before, and it looks like I cannot help with diagnosing this error. Hopefully somebody a little cleverer than myself can help out.

A parting suggestion: have you thought of posting a similar question on:

fetchmail-users -- 
[http://lists.berlios.de/mailman/listinfo/fetchmail-users](http://lists.berlios.de/mailman/listinfo/fetchmail-users)

as the fetchmail developers can be found there and should have a good idea what is going on.

Apologies,

Andrew

---

### Post by AlexBooton on 2009-08-19
Hi Andrew,

Absolutely no need to apologize!  You took your time, gave my the benefit of your expertise, and I truly appreciate that.

I'll follow your suggestion.

Thanks,

Alex


> **andrew.46 said:**
> Hi AlexBooton,

My apologies but I have had a long look at fetchmail + multidrop, an aspect of fetchmail usage I have not considered before, and it looks like I cannot help with diagnosing this error. Hopefully somebody a little cleverer than myself can help out.

A parting suggestion: have you thought of posting a similar question on:

fetchmail-users -- 
[http://lists.berlios.de/mailman/listinfo/fetchmail-users](http://lists.berlios.de/mailman/listinfo/fetchmail-users)

as the fetchmail developers can be found there and should have a good idea what is going on.

Apologies,

Andrew

---


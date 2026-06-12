---
title: "Fetchmail/Postfix and POP problem"
date: 2006-02-07
forum: General Help
---

### Post by bhogg on 2006-02-07
Hi,

This is a bit of a strange problem, and perhaps someone who knows more about POP3 can help with this.

The power supply died on my main computer, forcing me to check the mail I normally receive through fetchmail/postfix by simply logging in with Thunderbird (windows) and leaving messages on server (unless deleted).  I then reconnect the main computer, and for some reason fetchmail ignores messages seen by thunderbird and only retrieves newer messages.  Even unread messages that I saw the headers for in thunderbird are not retrieved.

So what options, if any, would force fetchmail to retrieve any messages sitting in the mailbox, regardless if they were processed and left there or not?

A bit from my .fetchmailrc:

```
set postmaster "bhogg"
set bouncemail
set no spambounce
set properties ""
set daemon 5
poll mail.********.com with proto POP3 auth password user "*****" there with password "*******" is bhogg here options warnings 3600
```

Any ideas?

Thanks,
Brian

---


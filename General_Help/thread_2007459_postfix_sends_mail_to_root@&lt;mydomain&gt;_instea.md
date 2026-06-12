---
title: "postfix sends mail to root@&lt;mydomain&gt; instead of root@localhost?"
date: 2012-06-20
forum: General Help
---

### Post by AlexBooton on 2012-06-20
Hi,

As the subject says, it appears postfix is trying to send mail to [email]root@sample.com[/email] instead of root@localhost.

Since I have no such email account with my ISP, I never see the mail.

I don't know where this mail is being generated from.  Could be cron, postfix or some other process but since I don't see it I'm left to guess.

Where is the setting to determine where root's mail is supposed to go?

Thanks,

AB

---

### Post by spikoley on 2012-06-20
It has been a long time since I set up Postfix, but this might help you.

```


**[Delivering some but not all accounts locally]("http://www.postfix.org/STANDARD_CONFIGURATION_README.html#some_local")**

A drawback of sending mail as "user@example.com" (instead of "user@hostname.example.com") is that mail for "root" and other system accounts is also sent to the central mailhost. In order to deliver such accounts locally, you can set up virtual aliases as follows:

1 /etc/postfix/main.cf:
2     virtual_alias_maps = hash:/etc/postfix/virtual
3 
4 /etc/postfix/virtual:
5     root     root@localhost
6     . . .
Translation:

Line 5: As described in the virtual(5) manual page, the bare name "root" matches "root@site" when "site" is equal to $myorigin, when "site" is listed in $mydestination, or when it matches $inet_interfaces or $proxy_interfaces.

Execute the command "postmap /etc/postfix/virtual" after editing the file.


```

If that doesn't help then check the rest of [this page]("http://www.postfix.org/STANDARD_CONFIGURATION_README.html").

---

### Post by SeijiSensei on 2012-06-20
Postfix, like sendmail, uses /etc/aliases.  Do you see an entry for root in the left-hand column of that file?

You can repoint the root mailbox to a valid address by editing /etc/aliases and adding or editing the entry for root so it looks like this:

```
root:     me@example.com
```

obviously replacing "me@example.com" with your actual address.  After you save the file, run the command "sudo newaliases" to rebuild the alias database.

---

### Post by AlexBooton on 2012-06-20
Thank you both for your help.  

I appreciate it.


AB

---


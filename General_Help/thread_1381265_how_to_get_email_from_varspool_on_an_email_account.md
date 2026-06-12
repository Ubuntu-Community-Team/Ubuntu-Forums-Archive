---
title: "how to get email from /var/spool on an email account"
date: 2010-01-14
forum: General Help
---

### Post by al_mic on 2010-01-14
hello,

does anyone know a way (the simple the better) to receive all the email that can be found in /var/spool/mail/user to a yahoo or gmail account?

i mean, instead of login to the server and read the messages from /var/spool/root, it will be a lot easyear and faster to found about them, if they will be sent to my email account

i know i can make the cron output be sent by email, if i place in front of the cron line something like :
MAILTO="email@something.com"

but in /var/spool/mail/ for root or other usernames you can found many other messages

so, any ideas?

thank you!

---

### Post by t0p on 2010-01-14
I'm afraid I don't know much about running an email server.  But I would imagine that you can set your email account on the server to forward all mail to your yahoo or gmail account. This would involve accessing the settings of the email account that is on that server.  Precise instructions would depend on the exact server software I should imagine.

It also depends on *how* you are accessing your email.  For instance, I get my mail from gmail accounts by using Evolution on my desktop machine; and I also have Evolution fetch mail from /var/spool/mail/user on the localhost.  You could do something similar, but fetching it from the mail server rather than the local machine (assuming the mail server isn't the local machine - if it is, you can just do exactly what I do).

But if you want the mail from the server to be accessible via your gmail/yahoo webmail interface, you need to tell the server to forward it.

---

### Post by al_mic on 2010-01-14
in /var/spool/mail you get all kind of messages.
another very interesting file to get by email would be the one from logwatch

the messages in /var/spool/mail/root for example are destined to root@localservername
it would be really nice if instead of append them in this file (/var/spool/mail/root) they will go to my email account from somewhere (yahoo, or other)

---

### Post by al_mic on 2011-12-19
I found the way to receive those emails.

If you have messages in /var/spool/mail/ and you want to get them as soon as they are being placed there, you'll have to do this:

- edit /etc/aliases and add a line for each username found in /var/spool/mail/
- for example if you only want to receive email for root make sure you have these lines:

postmaster:    root
root: [email]you@gmail.com[/email]

If you have other services installed, like clamav (the antivirus) which also can send emails to root, then you can have these lines:


postmaster:    root
clamav: root
root: [email]you@gmail.com[/email]

But you can also have:
john:           [EMAIL="john@gmail.com"]john@gmail.com[/EMAIL] 


Bottom line, for each user on the system you can define a redirect to another email address, or to another user on the system that will in the end send the mail to that address.

After you are done editing the /etc/aliases file you must run this:
# newaliases 

This is all.


One more thing I am trying to find is how to get the message to my external email address, but also keep a copy of them on that server.

I found a way by creating new users and then defining redirects to both the new local user and to my external email address, like this:

postmaster:    root, backup_user
root: [email]you@gmail.com[/email]

But I do not like this method because I have to create a new user for each email redirect.

If you know a better way, please tell me.

Thanks.

---

### Post by Teh_Messiah on 2012-03-19
Ok I edited the aliases file to
```
postmaster:    root, www-data
root:   myemailaddress@hotmail.com
```

[LIST=1]
[*]Is this correct?
[*]How can I test it to make sure it's working?
[*]If it doesn't work, How do I fix it?
[/LIST]

I set up smartmontools which says it sends error reports for my mdadm to an email address which I specified in the /etc/smartd.conf file but nothing has been sent.

---


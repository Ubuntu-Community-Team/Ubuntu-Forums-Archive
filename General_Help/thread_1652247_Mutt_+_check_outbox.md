---
title: "Mutt + check outbox"
date: 2010-12-24
forum: General Help
---

### Post by genjix on 2010-12-24
Hey,

I'm using Mutt to read my email, together with ssmtp to send.

/etc/ssmtp/ssmtp.conf
```
root=root
mailhub=mail.riseup.net:25
rewriteDomain=riseup.net
hostname=l
AuthUser=loginname
AuthPass=mypassword
UseTLS=YES
UseSTARTTLS=YES

```

~/.muttrc
```
set ssl_starttls=no

set spoolfile='imap://mail.riseup.net/INBOX'   # where my new mail is located

set imap_user = myusername
set imap_pass= mypassword ;)
set imap_passive=yes
set imap_servernoise=no

send-hook . "set record=imaps://mail.riseup.net/INBOX.Sent"
set record ="imaps://mail.riseup.net/INBOX.Sent"

unset bounce_delivered
unset use_domain
unset user_agent
unset use_from
```

1) The sent mail is stored on the remote server. I'm able to login using their webmail and read it. How can I check it using imap?

2) Mutt creates ~/Mail/ <- how can I change this directory to ~/.mail/ ?

Thanks

---

### Post by genjix on 2010-12-24
```
set folder="imaps://mail.riseup.net/INBOX.Sent"
mailboxes +folder

```

That's the solution, heh :)

Still looking to see if I've done it correctly or other ideas.

---


---
title: "postfix + dovecot + smtp authentication"
date: 2009-11-04
forum: General Help
---

### Post by Nstuff on 2009-11-04
Hello,

I am getting insane, It feels like I have done this so many times, that I most likely starting to miss something simple but I can't figure out what.. hopefully someone can share his lightbulb and replace my not working lightbulb :D

My want to have setup is:

Ubuntu 9.10, which has been upgraded from 7.04 (through 7.10, 8.04 etc etc)
- Postfix - connecting to mysql for user information (working)
- Dovecot (pop3/imap) - connecting to mysql for user information (working)
- Dovecot (LDA) - for delivery to the maildirs (working)
- Dovecot (smtp authentication) -> not working

My problem is that I can't seem to get STMP authentication to work. I always used postfix + maildrop + courier + sasl and this worked pretty ok. For this server I de-installed courier, maildrop and sasl and tried building the same thing with dovecot, which makes my life easier on the long run I hope.

I used the simple setup from dovecot that has been explained on [http://wiki.dovecot.org/HowTo/PostfixAndDovecotSASL](http://wiki.dovecot.org/HowTo/PostfixAndDovecotSASL)
As explained there, what could go wrong there... it sounds too easy.

Anyway, after making my configuration changes, I restarted postfix/dovecot and trying to see if it works. Making a telnet to the server shows me the following:

220 mail.domain.com ESMTP Postfix (Ubuntu)
ehlo localhost
250-mail.domain.com
250-PIPELINING
250-SIZE 20480000
250-VRFY
250-ETRN
250-STARTTLS
250-ENHANCEDSTATUSCODES
250-8BITMIME
250 DSN

Which means the auth login is not supported, since its not started. What did I miss?
My configuration of the postfix contains the following:

```
smtpd_sasl_auth_enable = yes
smtpd_sasl_type = dovecot
smtpd_sasl_path = private/auth

# modify the existing smtpd_recipient_restrictions
smtpd_recipient_restrictions = reject_unknown_sender_domain, reject_unknown_recipient_domain, reject_unauth_pipelining, permit_mynetworks, permit_sasl_authenticated, reject_unauth_destination
```My dovecot configuration contains:

```
auth default {
mechanisms = plain login
  # SQL database <doc/wiki/AuthDatabase.SQL.txt>
  passdb sql {
    # Path for SQL configuration file
    args = /etc/dovecot/dovecot-sql.conf
  }
  # SQL database <doc/wiki/AuthDatabase.SQL.txt>
  userdb sql {
    # Path for SQL configuration file
    args = /etc/dovecot/dovecot-sql.conf
  }
user = root
  socket listen {
    master {
      # Master socket provides access to userdb information. It's typically
      # used to give Dovecot's local delivery agent access to userdb so it
      # can find mailbox locations.
      path = /var/run/dovecot/auth-master
      mode = 0660
      # Default user/group is the one who started dovecot-auth (root)
      user = vmail
      group = vmail
    }
    client {
      # The client socket is generally safe to export to everyone. Typical use
      # is to export it to your SMTP server so it can do SMTP AUTH lookups
      # using it.
        path = /var/spool/postfix/private/auth
        mode = 0660
        user = postfix
        group = postfix
    }
  }
}

```Basically I am missing why the SASL is not starting. Incase anyone is wondering, /var/spool/postfix/private/auth is created when dovecot or postfix is restarted. 

Thanks for your time and answers!

---

### Post by ayesiloz on 2009-12-26
i have same problem if you found solituon please share

---


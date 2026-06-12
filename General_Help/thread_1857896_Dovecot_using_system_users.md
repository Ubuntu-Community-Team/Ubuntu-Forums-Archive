---
title: "Dovecot using system users"
date: 2011-10-11
forum: General Help
---

### Post by vitotol on 2011-10-11
Hello I have a server with dovecot set up for virtual users. I want to configure it so I can download my system users email on thunderbird.

Below is my current config:

```

base_dir = /var/run/dovecot/
listen = *
log_path = /var/log/dovecot
mail_location = mbox:/var/spool/mail:INBOX=/var/spool/mail/%u
#mail_location = mbox:/var/spool/mail/%u

protocols = imap imaps pop3 pop3s
disable_plaintext_auth = no
log_path = /var/log/dovecot.log
protocol imap {
}
protocol pop3 {
}
auth default {
  mechanisms = plain
  passdb passwd-file {
    args = /etc/dovecot_passwd
  }
passdb shadow {
}
  userdb passwd-file {
    args = /etc/dovecot_passwd
  }
user = root
}
plugin {
}

pop3_uidl_format = %08Xu%08Xv

```

---

### Post by vitotol on 2011-10-11
I managed to solve this issue.
I found all the information here.
[http://www.dslreports.com/forum/r19561703-SOLVED-Dovecot-PAM](http://www.dslreports.com/forum/r19561703-SOLVED-Dovecot-PAM)...

---


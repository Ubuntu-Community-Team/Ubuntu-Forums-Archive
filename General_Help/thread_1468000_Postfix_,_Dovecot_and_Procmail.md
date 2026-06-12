---
title: "Postfix , Dovecot and Procmail"
date: 2010-05-01
forum: General Help
---

### Post by stefanfa on 2010-05-01
Hi.

I've installed Postfix, Dovecot and Procmail.
And i want to have procmail parse my mails.
I've searched the internet about getting this to work without results.

I've come this far atm:

/etc/postfix/main.cf:
---------------------
mailbox_command = /usr/bin/procmail -t -a "$EXTENSION"

/etc/procmailrc:
----------------
SHELL="/bin/bash"
SENDMAIL="/usr/sbin/sendmail -oi -t"
LOGFILE="/var/log/procmail.log"
#DELIVER="/usr/lib/dovecot/deliver"
#DELIVER="/usr/lib/dovecot/deliver -c /etc/dovecot/conf.d/01-dovecot-postfix.conf"
DELIVER="/usr/lib/dovecot/deliver -c /etc/dovecot/conf.d/01-dovecot-postfix.conf -n -m '$1'"
# fallback:
DEFAULT="$HOME/Maildir/"
MAILDIR="$HOME/Maildir/"
:0 w
| $DELIVER

I get this error in procmail.log:
---------------------------------
Fatal: destination user parameter (-d user) not given
procmail: Program failure (64) of "/usr/lib/dovecot/deliver"


My mails still get delivered though.
And the users procmail files gets parsed aswell.
But i'm guessing it's the fallback that makes it work atm.

The reason i want to use procmail + sieve is that i got a procmail script that parses mails to files and sieve can't do that.

---

### Post by stefanfa on 2010-05-07
*bump*

---

### Post by max.brouwer on 2010-12-18
I just stumbled over the same error message and I've solved it by using an answer in wiki.dovecot.org stating that the deliver program expects a -d if running as root. Add DROPPRIVS=yes in your procmail.rc to prevent this error.

Probably to late for you, but it might help someone else.

Regards,

Max

---


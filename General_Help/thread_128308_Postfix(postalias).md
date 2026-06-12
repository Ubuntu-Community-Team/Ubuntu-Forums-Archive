---
title: "Postfix(postalias)"
date: 2006-02-11
forum: General Help
---

### Post by rensu on 2006-02-11
Im getting this error when typing postalias /etc/postfix/aliases

postalias: fatal: /etc/mailname: unable to open: cannot open file: No such file or directory
:confused:

Can anyone tell me how I can fix that?

---

### Post by heimo on 2006-02-11
[quote=rensu]Im getting this error when typing postalias /etc/postfix/aliases

postalias: fatal: /etc/mailname: unable to open: cannot open file: No such file or directory
:confused:

Can anyone tell me how I can fix that?[/quote]

Create /etc/mailname file with your systems "mail name", part after @ - typically your domain name.

> 
MAILNAME(5)               Linux System Administration              MAILNAME(5)

NAME
       mailname - the visible mail name of the system

DESCRIPTION
       The  file /etc/mailname is a plain ASCII configuration file, which on a
       Debian system contains the visible mail name of the system.  It is used
       by many different programs, usually programs that wish to send or relay
       mail, and need to know the name of the system.

       The file contains only one line describing the fully  qualified  domain
       name that the program wishing to get the mail name should use (that is,
       everything after the @).


---

### Post by rensu on 2006-02-11
Oh thnx:P My wrong. I have deleted the file before i guess.:p

---


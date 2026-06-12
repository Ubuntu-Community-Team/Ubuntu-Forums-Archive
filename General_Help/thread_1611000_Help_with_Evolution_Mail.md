---
title: "Help with Evolution Mail"
date: 2010-11-01
forum: General Help
---

### Post by fmuise on 2010-11-01
How do I specify ports for the IMAP server and the SMTP server.

Also there's no where to put my password in, just a checkbox to remember my password, what password?

I'm trying to configure Evolution with GMAIL, as I really don't like Thundermail as my main mail client.#-o

---

### Post by gandaran on 2010-11-01
> **fmuise said:**
> How do I specify ports for the IMAP server and the SMTP server.

Also there's no where to put my password in, just a checkbox to remember my password, what password?

I'm trying to configure Evolution with GMAIL, as I really don't like Thundermail as my main mail client.#-o
theres no need to specify ports, gmail in evolution is almost automatically setup, just enter you email account and choose SSL encryption for receiving and outgoing mail.
evolution will ask for the password when you try to access mail.

---

### Post by fmuise on 2010-11-01
hmmm, will do although that is how it's currently setup.

I'll double check everything though, 

Thanks!

---

### Post by plucky on 2010-11-01
> How do I specify ports for the IMAP server and the SMTP server.


For my IMAP I use ```
smtp.gmail.com:465
imap.gmail.com:993
``` where the port numbers are 465 and 993.

Good Luck

---

### Post by Z06Gal on 2010-11-01
I went by this and it works great:

[http://linuxowns.wordpress.com/2009/03/04/setting-up-evolution-mail-gmail-and-hotmail/](http://linuxowns.wordpress.com/2009/03/04/setting-up-evolution-mail-gmail-and-hotmail/)

---

### Post by lisati on 2010-11-01
> **fmuise said:**
> Also there's no where to put my password in, just a checkbox to remember my password, what password?

Probably your password on the email server. Evolution is likely to prompt you and let you type one in when you check your email for the first time.

---


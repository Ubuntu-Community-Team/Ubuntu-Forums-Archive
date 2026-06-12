---
title: "/usr/bin/mail to use Postfix"
date: 2011-09-11
forum: General Help
---

### Post by ssppune on 2011-09-11
Hi
I have configured Postfix on Ubuntu 11.04. Mutt is working fine.
Some of my old scripts using /usr/bin/mail (which was for sendmail). But /usr/bin/mail is not working with postfix.
Do i need to install sendmail in order to use /usr/bin/mail? i donot think so.

please guide if my Mutt is working , how can i make /usr/bin/mail workable? what are the configuration files need to edit , especially for sender email id , domain name , relay etc?

---

### Post by dcstar on 2011-09-12
> **ssppune said:**
> Hi
I have configured Postfix on Ubuntu 11.04. Mutt is working fine.
Some of my old scripts using /usr/bin/mail (which was for sendmail). But /usr/bin/mail is not working with postfix.
Do i need to install sendmail in order to use /usr/bin/mail? i donot think so.

please guide if my Mutt is working , how can i make /usr/bin/mail workable? what are the configuration files need to edit , especially for sender email id , domain name , relay etc?

Install the **bsd-mailx** package.

---


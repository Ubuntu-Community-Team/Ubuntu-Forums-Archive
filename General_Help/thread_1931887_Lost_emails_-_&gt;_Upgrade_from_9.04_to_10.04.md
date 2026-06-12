---
title: "Lost emails - &gt; Upgrade from 9.04 to 10.04"
date: 2012-02-26
forum: General Help
---

### Post by zigam on 2012-02-26
I had Ubuntu 9.04 Server and I didn't have program to have SMTP support, and I couldn't install it with apt-get (because 9.04 is too old?) and so I upgraded with do-release-upgrade.

After that, mail didn't work anymore, so I did this:
apt-get purge dovecot-common dovecot-imapd dovecot-pop3d dovecot-postfix postfix ssl-cert
apt-get install dovecot-postfix.

After that, mail works again, but there is no old emails.
In home folders of users there is created a map Maildir, but before that mail was in two maps. /home/user/mail (which contained Drafts,Junk,Spam and Trash) and in /var/mail/user (which contained file with name user and there was Inbox).

How can I use old emails with new system?

---

### Post by zigam on 2012-02-26
That did the trick, but I am still hoping for better approach :)

awk -vRS="From " '{print "From "$0>NR".txt"}' file-name

---


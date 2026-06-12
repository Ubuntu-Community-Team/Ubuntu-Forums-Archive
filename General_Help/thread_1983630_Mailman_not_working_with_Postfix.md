---
title: "Mailman not working with Postfix"
date: 2012-05-20
forum: General Help
---

### Post by absoord on 2012-05-20
Hey!

Now that I have mi Postfix + Dovecot running, I'm trying to configure mailman so I can handle mail lists. Let's suppose the machine running postfix (with MySQL support for virtual accounts) + dovecot + mailman is mail.mydomain.es, so my uplevel domain is mydomain.es

My idea was to create e-mail accounts like [email]mark@mydomain.es[/email], [email]susan@mydomain.es[/email], etc. It's ok, That's working.

The problem comes with mailman. If I configure a mail list to be sent from [email]mylist@lists.mydomain.es[/email], there's no trouble in that. But I want to create lists with the uplevel domain, something like [email]list1@mydomain.es[/email], [email]list2@mydomain.es[/email]. And there's the problem, so under mydomain.es I have both virtual accounts and mail lists. Anytime I try to send an e-mail to a **list** at mydomain.es, I get the following error:

```

May 20 19:04:14 mail postfix/smtpd[9199]: NOQUEUE: reject: RCPT from unknown[192.168.0.10]: 550 5.1.1 <myname@mydomain.es>: Recipient address rejected: User unknown in virtual mailbox table; from=<myname@mydomain.es> to=<mylist@mydomain.es> proto=ESMTP helo=<[192.168.0.10]>

```

That doesn't happen on real e-mail accounts, e-mails are delivered correctly. I'm really stucked with that, I don't really know it's an Postfix config error or a mailman config error. It looks quite clear postfix's trying to get that user from its database and -of course- it doesn't exist as it's an alias for a mailman list, but shouldn't postfix try to associate it to mailman if the database search fails?

There are my config files:

/etc/postfix/main.cf:

```

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no
append_dot_mydomain = no
readme_directory = /usr/share/doc/postfix

# TLS parameters
smtpd_tls_cert_file = /etc/postfix/smtpd.cert
smtpd_tls_key_file = /etc/postfix/smtpd.key
smtpd_use_tls = yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

myhostname = mail.mydomain.es
alias_maps = hash:/etc/aliases, hash:/var/lib/mailman/data/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = mail.mydomain.es, localhost, localhost.localdomain
relayhost = [mydomain.es]
mynetworks = 127.0.0.0/8 192.0.0.0/8
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
html_directory = /usr/share/doc/postfix/html
message_size_limit = 30720000
virtual_alias_domains =
virtual_alias_maps = proxy:mysql:/etc/postfix/mysql-virtual_forwardings.cf, mysql:/etc/postfix/mysql-virtual_email2email.cf
virtual_mailbox_domains = proxy:mysql:/etc/postfix/mysql-virtual_domains.cf
virtual_mailbox_maps = proxy:mysql:/etc/postfix/mysql-virtual_mailboxes.cf
virtual_mailbox_base = /home/vmail
virtual_uid_maps = static:5000
virtual_gid_maps = static:5000

###############
smtpd_sasl_auth_enable = no
broken_sasl_auth_clients = yes
smtpd_sasl_authenticated_header = yes
smtpd_recipient_restrictions = permit_mynetworks, permit_sasl_authenticated, reject_unauth_destination
proxy_read_maps = $local_recipient_maps $mydestination $virtual_alias_maps $virtual_alias_domains $virtual_mailbox_maps $virtual_mailbox_domains $relay_recipient_maps $relay_domains $canonical_maps $sender_canonical_maps $recipient_canonical_maps $relocated_maps $transport_maps $mynetworks $virtual_mailbox_limit_maps
virtual_transport = dovecot

# E-mail lists with mailman
mailman_destination_recipient_limit = 1
unknown_local_recipient_reject_code = 550
owner_request_special = no

```

/etc/postfix/master.cf

```

mailman   unix  -       n       n       -       -       pipe
  flags=FR user=list argv=/usr/lib/mailman/bin/postfix-to-mailman.py ${nexthop} ${user}

```

/etc/mailman/mm_cfg.py

```

from Defaults import *

MAILMAN_SITE_LIST = 'mailman'

DEFAULT_URL_PATTERN = 'http://%s/cgi-bin/mailman/'
PRIVATE_ARCHIVE_URL = '/cgi-bin/mailman/private'
IMAGE_LOGOS         = '/images/mailman/'

DEFAULT_EMAIL_HOST = 'mydomain.es'
DEFAULT_URL_HOST   = 'mydomain.es'
add_virtualhost(DEFAULT_URL_HOST, DEFAULT_EMAIL_HOST)

DEFAULT_SERVER_LANGUAGE = 'es'

USE_ENVELOPE_SENDER    = 0              # Still used?
DEFAULT_SEND_REMINDERS = 0
MTA='Postfix'

POSTFIX_ALIAS_CMD = '/usr/sbin/postalias'
POSTFIX_MAP_CMD = '/usr/sbin/postmap'

```

Any help will be highly appreciated!! :-)

Thanx!!

---


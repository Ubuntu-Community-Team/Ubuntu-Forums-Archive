---
title: "Help with simple Unbuntu Mail Server (postfix"
date: 2011-12-15
forum: General Help
---

### Post by jspiegel187 on 2011-12-15
Hey, I'm having trouble getting the basic mail server running. I can telnet in but when I try to send an email the "RCPT TO:" portion denies it no matter what I type in. Below is the tail of the mail log:

Dec 15 12:13:20 zero postfix/smtpd[2304]: connect from localhost.localdomain[127.0.0.1]
Dec 15 12:14:05 zero postfix/smtpd[2304]: NOQUEUE: reject: RCPT from localhost.localdomain[127.0.0.1]: 554 5.7.1 <localhost.localdomain[127.0.0.1]>: Client host rejected: Access denied; from=<master@zero.local> to=<jripeastwest@yahoo.com> proto=ESMTP helo=<zero.local>
Dec 15 12:14:05 zero postfix/smtpd[2304]: warning: restriction `rbl_client' after `reject' is ignored
Dec 15 12:14:08 zero postfix/smtpd[2304]: disconnect from localhost.localdomain[127.0.0.1]

My username on the box is "master" and my hostname is zero.local 
The firewall is closed as per the instructions.

Below is my main.cf


# See /usr/share/postfix/main.cf.dist for a commented, more complete version


# Debian specific: Specifying a file name will cause the first
# line of that file to be used as the name. The Debian default
# is /etc/mailname.
#myorigin = /etc/mailname
myorigin= zero.local


smtpd_banner = $myhostname ESMTP Welcome, XNasty at your service.....
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

readme_directory = no

# TLS parameters
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname =zero.local
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = zero.local, zero, localhost.localdomain, localhost
relayhost =smtp-server.nyc.rr.com
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
mynetworks_style = host
masquerade_domains =
masquerade_exceptions = rootlocal_recipient_maps =
mydestination =

# MAIL SETTINGS

delay_warning_time = 4h
unknown_local_recipient_reject_code = 450
maximal_queue_lifetime = 7d
minimal_backoff_time = 1000s
maximal_backoff_time = 8000s
smtp_helo_timeout = 60s
smtpd_recipient_limit = 16
smtpd_soft_error_limit = 3
smtpd_hard_error_limit = 12


# RESTRICTIONS

smtpd_helo_restrictions = permit_mynetworks, warn_if_reject reject_non_fqdn_hostname, reject_invalid_hostname, permit
#

smtpd_sender_restrictions = permit_mynetworks, warn_if_reject reject_non_fqdn_sender, reject_unknown_sender_domain, reject_unauth_pipelining, permit


smtpd_client_restrictions = reject_rbl_client sbl.spamhaus.org, reject rbl_client blackholes.easynet.nl, reject_rbl_client dnsbl.njabl.org

smtpd_recipient_restrictions = reject_unauth_pipelinig, permit_mynetworks, reject_non_fqdn_recipient, reject_unknown_recipient_domain, reject_unauth_destination, permit

smtpd_data_restrictions = reject_unauth_pipelining

smptd_helo_required = yes

smptd_delay_reject = yes

disable_vrfy_command = yes

#######

alias_maps = hash:/etc/postfix/aliases
alias_database = hash:/etc/postfix/aliases
virtual_mailbox_base = /var/spool/mail/virtual
virtual_mailbox_maps = mysql:/etc/postfix/mysql_mailbox.cf
virtual_alias_maps = mysql:/etc/postfix/mysql_alias.cf
virtual_mailbox_domains = mysql:/etc/postfix/mysql_domains.cf
virtual_uid_maps = static:5000
virtual_gid_maps = static:5000


I'd love to get this running. Not sure what the next step is to get this past the testing phase.

Any help is appreciated..:o

---

### Post by dcstar on 2011-12-17
> **jspiegel187 said:**
> Hey, I'm having trouble getting the basic mail server running. I can telnet in but when I try to send an email the "RCPT TO:" portion denies it no matter what I type in. Below is the tail of the mail log:

Dec 15 12:13:20 zero postfix/smtpd[2304]: connect from localhost.localdomain[127.0.0.1]
Dec 15 12:14:05 zero postfix/smtpd[2304]: NOQUEUE: reject: RCPT from localhost.localdomain[127.0.0.1]: 554 5.7.1 <localhost.localdomain[127.0.0.1]>: Client host rejected: Access denied; from=<master@zero.local> to=<jripeastwest@yahoo.com> proto=ESMTP 
.........
I'd love to get this running. Not sure what the next step is to get this past the testing phase.

Any help is appreciated..:o

[LIST=1]
[*]Put code inside "Code" tags.
[*]Fix this:
```
masquerade_exceptions = rootlocal_recipient_maps =
```
[*]Do this and put your local network in:
```
sudo dpkg-reconfigure postfix
```
[/LIST]

---


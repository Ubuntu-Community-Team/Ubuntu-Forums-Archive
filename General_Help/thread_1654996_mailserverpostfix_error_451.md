---
title: "mailserver/postfix error 451"
date: 2010-12-29
forum: General Help
---

### Post by engelienart on 2010-12-29
Hi,

I have a postfix mailserver up and running.
I tried to send an email using telnet, but I get an error:
This is what I do:

```
telnet localhost 25
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
220 dag-pdc.localdomain ESMTP Postfix
EHLO smtp.local.dag
250-dag-pdc.localdomain
250-PIPELINING
250-SIZE 10240000
250-ETRN
250-STARTTLS
250-ENHANCEDSTATUSCODES
250-8BITMIME
250 DSN
MAIL FROM: sender@******.nl
250 2.1.0 Ok
RCPT TO: receptant@******.com
451 4.3.5 Server configuration error
421 4.4.2 dag-pdc.localdomain Error: timeout exceeded
```(the ****** is my emailadress, not for spying eyes)

I have found a same thread in your archives, but the solution did not work for me.
Does anybode know what is wrong?

Here is my /etc/postfix/main.cf

```
# See /usr/share/postfix/main.cf.dist for a commented, more complete version


# Debian specific:  Specifying a file name will cause the first
# line of that file to be used as the name.  The Debian default
# is /etc/mailname.
#myorigin = /etc/mailname

smtpd_banner = $myhostname ESMTP $mail_name
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
delay_warning_time = 4h
# will it be a permanent error or temporary
unknown_local_recipient_reject_code = 450
# how long to keep message on queue before return as failed. 
# some have 3 days, I have 16 days as I am backup server for some people
# whom go on holiday with their server switched off.
maximal_queue_lifetime = 7d
# max and min time in seconds between retries if connection failed
minimal_backoff_time = 1000s
maximal_backoff_time = 8000s
# how long to wait when servers connect before receiving rest of data
smtp_helo_timeout = 60s
# how many address can be used in one message.
# effective stopper to mass spammers, accidental copy in whole address list
# but may restrict intentional mail shots.
smtpd_recipient_limit = 16
# how many error before back off.
smtpd_soft_error_limit = 3
# how many max errors before blocking it.
smtpd_hard_error_limit = 12

# TLS parameters
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${queue_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${queue_directory}/smtp_scache

# Op hoop van zegen
# smtpd_restriction_classes = restrictive, permissive
    # With Postfix < 2.3 specify reject_unknown_client.
#    restrictive = reject_unknown_sender_domain reject_unknown_client_hostname ...
#    permissive = permit

# smtpd_recipient_restrictions = 
#    permit_mynetworks
#    reject_unauth_destination
#    check_recipient_access hash:/etc/postfix/recipient_access

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

# mijn domeinnaam (Laptop Vista is geen lid van domein?)
# myhostname = smtp.local.dag
mynetworks = 128.10.1.0/24, 89.200.80.237, 86.80.86.55

alias_maps = hash:/etc/postfix/aliases
alias_database = hash:/etc/postfix/aliases
# this specifies where the virtual mailbox folders will be located
virtual_mailbox_base = /var/spool/mail/virtual
# this is for the mailbox location for each user
virtual_mailbox_maps = mysql:/etc/postfix/mysql_mailbox.cf
# and their user id
virtual_uid_maps = mysql:/etc/postfix/mysql_uid.cf
# and their group id
virtual_gid_maps = mysql:/etc/postfix/mysql_gid.cf
# and this is for aliases
virtual_alias_maps = mysql:/etc/postfix/mysql_alias.cf
# and this is for domain lookups
virtual_mailbox_domains = mysql:/etc/postfix/mysql_domain.cf
# this is how to connect to the domains (all virtual, but the option is there)
# not used yet
# transport_maps = mysql:/etc/postfix/mysql_transport.cf

myorigin = local.dag
mydestination = smtp.local.dag
mailbox_size_limit = 0
recipient_delimiter = +
inet_protocols = all
relayhost = smtp.zakelijkmail.nl
# tips van: flurdy.com/docs/postfix/#config-simple-mta
inet_interfaces = all
mynetworks_style = host
# masquerade_domains = smtp.local.dag www.local.dag !sub.dyndomain.com
# masquerade_exceptions = root
local_recipients_maps =
mydestination =


# security
smtpd_recipient_limit = 100
# tips van: www.freesoftwaremagazine.com/articles/focus_spam_postfix
smtpd_delay_reject = yes
smtpd_helo_required = yes
disable_vrfy_command = yes
# Requirements for the HELO statement
smtpd_helo_restrictions = permit_mynetworks, warn_if_reject reject_non_fqdn_hostname, reject_invalid_hostname, permit
# Requirements for the sender details
smtpd_sender_restrictions = permit_mynetworks, warn_if_reject reject_non_fqdn_sender, reject_unknowm_sender_domain, reject_unauth_pipelining, permit
# Requirements for the connecting servers
smtpd_client_restrictions = reject_rbl_client sbl.spamhaus.org, reject_rbl_client blackholes.easynet.nl, reject_rbl_client dnsbl.njabl.org
# Requirements for the recipient address
smtpd_recipient_restrictions = reject_unauth_pipelining, permit_mynetworks, reject_non_fqdn_recipient, reject_unknown_recipient_domain, reject_unauth_destination, permit
smtpd_data_restrictions = reject_unauth_pipelining

#    check_helo_access 
#           hash:/usr/local/etc/postfix/helo_access,
#         reject_non_fqdn_hostname,
#         reject_invalid_hostname,
#         permit
```

---


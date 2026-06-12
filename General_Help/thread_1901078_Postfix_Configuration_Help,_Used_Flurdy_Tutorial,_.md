---
title: "Postfix Configuration Help, Used Flurdy Tutorial, PLEASE HELP"
date: 2011-12-27
forum: General Help
---

### Post by jspiegel187 on 2011-12-27
Hey folks, I wanted to try the flurdy tutorial on installing postfix with all of it's add-ons. The main system is installed but I'm getting errors when I telnet into the box and try to send or receive mail. Please see my postconf information below:

alias_database = hash:/etc/postfix/aliases
alias_maps = hash:/etc/postfix/aliases
append_dot_mydomain = no
biff = no
config_directory = /etc/postfix
delay_warning_time = 4h
disable_vrfy_command = yes
inet_interfaces = all
local_recipient_maps = 
mailbox_size_limit = 0
masquerade_domains = 
masquerade_exceptions = root
maximal_backoff_time = 8000s
maximal_queue_lifetime = 7d
minimal_backoff_time = 1000s
mydestination = 
myhostname = zero.local
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mynetworks_style = host
myorigin = /etc/mailname
readme_directory = no
recipient_delimiter = +
relayhost = smtp-server.nyc.rr.com
smtp_helo_timeout = 60s
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache
smtpd_banner = $myhostname ESMTP $mail_name
smtpd_client_restrictions = reject_rbl_client sbl.spamhaus.org, reject_rbl_client blackholes.easynet.nl, reject_rbl_client dnsbl.njabl.org
smtpd_data_restrictions = reject_unauth_pipelining
smtpd_hard_error_limit = 12
smtpd_helo_restrictions = permit_mynetworks, warn_if_reject reject_non_fqdn_hostname, reject_invalid_hostname, permit
smtpd_recipient_limit = 16
smtpd_recipient_restrictions = reject_unauth_pipelinig, permit_mynetworks, reject_non_fqdn_recipient, reject_unknown_recipient_domain, reject_unauth_destination, permit
smtpd_sender_restrictions = permit_mynetworks, warn_if_reject reject_non_fqdn_sender, reject_unknown_sender_domain, reject_unauth_pipelining, permit
smtpd_soft_error_limit = 3
smtpd_tls_cert_file = /etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file = /etc/ssl/private/ssl-cert-snakeoil.key
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtpd_use_tls = yes
unknown_local_recipient_reject_code = 450
virtual_alias_maps = mysql:/etc/postfix/mysql_alias.cf
virtual_gid_maps = static:5000
virtual_mailbox_base = /var/spool/mail/virtual
virtual_mailbox_domains = mysql:/etc/postfix/mysql_domains.cf
virtual_mailbox_maps = mysql:/etc/postfix/mysql_mailbox.cf
virtual_uid_maps = static:5000


And here is my main.cf

# Debian specific:  Specifying a file name will cause the first
# line of that file to be used as the name.  The Debian default
# is /etc/mailname.
myorigin = /etc/mailname

###############
#SMTPD BANNER#
###############

smtpd_banner = $myhostname ESMTP $mail_name
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

readme_directory = no

###############
# TLS parameters#
###############

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
masquerade_exceptions = root
local_recipient_maps =
mydestination =

###############
# MAIL SETTINGS #
###############


delay_warning_time = 4h
unknown_local_recipient_reject_code = 450
maximal_queue_lifetime = 7d
minimal_backoff_time = 1000s
maximal_backoff_time = 8000s
smtp_helo_timeout = 60s
smtpd_recipient_limit = 16
smtpd_soft_error_limit = 3
smtpd_hard_error_limit = 12

###############
# RESTRICTIONS #
###############


smtpd_helo_restrictions = permit_mynetworks, warn_if_reject reject_non_fqdn_host
name, reject_invalid_hostname, permit



smtpd_sender_restrictions = permit_mynetworks, warn_if_reject reject_non_fqdn_se
nder, reject_unknown_sender_domain, reject_unauth_pipelining, permit


smtpd_client_restrictions = reject_rbl_client sbl.spamhaus.org, reject_rbl_clien
t blackholes.easynet.nl, reject_rbl_client dnsbl.njabl.org


smtpd_recipient_restrictions = reject_unauth_pipelinig, permit_mynetworks, rejec
t_non_fqdn_recipient, reject_unknown_recipient_domain, reject_unauth_destination
, permit



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


What looks wrong?

-JMS

---


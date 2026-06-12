---
title: "Failed to connect access denied MySQL authdaemon"
date: 2010-01-21
forum: General Help
---

### Post by traxtermaster on 2010-01-21
Hi i just finish tring to get my mail server running but i get an error in my mail.log 

Jan 21 16:33:08 server imapd-ssl: Connection, ip=[::ffff:67.223.78.XX]
Jan 21 16:33:08 server authdaemond: failed to connect to mysql server (server=127.0.0.1, userid=postfixadmin): Access denied for user 'postfixadmin'@'localhost' (using password: YES)
Jan 21 16:33:08 server imapd-ssl: LOGIN FAILED, user=jason@[mydomain].com, ip=[::ffff:67.223.78.76]
Jan 21 16:33:08 server imapd-ssl: authentication error: Input/output error

I have the right password in all the mysql config files and tried to reset the password in the sql database with no luck. I granted perms to all and its still giving me the error

i hope some one can help me with that.

---

### Post by traxtermaster on 2010-01-21
I posted some more detail on the configuration i have. just hoping i could find the solution probably not much.

mysql_relay_domains_maps.cf

```
user = postfixadmin
password = "password"
hosts = 127.0.0.1
dbname = postfixadmin
table = domain
select_field = domain
where_field = domain
additional_conditions = and backupmx = '1'
```

main.cf

```
# See /usr/share/postfix/main.cf.dist for a commented, more complete version


# Debian specific:  Specifying a file name will cause the first
# line of that file to be used as the name.  The Debian default
# is /etc/mailname.
#myorigin = /etc/mailname

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h

readme_directory = /usr/share/doc/postfix

# TLS parameters
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = localhost
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
mydestination = server, localhost.localdomain, localhost, jasonmougeot.com
#relayhost =
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128, 192.168.1.0/24
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
html_directory = /usr/share/doc/postfix/html

# Virtual Mailbox Domain Settings

virtual_alias_maps = mysql:/etc/postfix/mysql_virtual_alias_maps.cf
virtual_mailbox_domains = mysql:/etc/postfix/mysql_virtual_domains_maps.cf
virtual_mailbox_maps = mysql:/etc/postfix/mysql_virtual_mailbox_maps.cf
virtual_mailbox_limit = 51200000
virtual_minimum_uid = 5000
virtual_uid_maps = static:5000
virtual_gid_maps = static:5000
virtual_mailbox_base = /home/vmail
virtual_transport = virtual

# Additional for quota support

virtual_create_maildirsize = yes
virtual_mailbox_extended = yes
virtual_mailbox_limit_maps = mysql:/etc/postfix/mysql_virtual_mailbox_limit_maps
.cf
virtual_mailbox_limit_override = yes
virtual_maildir_limit_message = Sorry, the your maildir has overdrawn your disks
pace quota, please free up some of spaces of your mailbox try again.
virtual_overquota_bounce = yes

#The host name where your MX for virtual domains will point to
#myhostname = mail.domain.com
#mydestination = #Remains blank since we are going to host virtual domains
#relayhost = #Remains blank unless you are going to use your ISP's SMTP server m
ail sending out mails. In which case it would be set to the host name of the ISP
's SMTP server

#smtpd_recipient_restrictions = reject_unauth_pipelining, permit_mynetworks, per
mit_sasl_authenticated, reject_non_fqdn_recipient, reject_unauth_destination, ch
eck_policy_service
# modify the existing smtpd_sender_restrictions
#smtpd_sender_restrictions = permit_sasl_authenticated, permit_mynetworks, rejec
t_non_fqdn_sender, reject_unknown_sender_domain, reject_unauth_pipelining, permi
t
# then add these
smtpd_sasl_auth_enable = yes
broken_sasl_auth_clients = yes
smtpd_sasl_path = /etc/postfix/sasl:/usr/lib/sasl2
smtpd_sasl_security_options = noanonymous
smtpd_sasl_local_domain =

```

smtpd.conf

```
pwcheck_method: auxprop
auxprop_plugin: sql
mech_list: plain login cram-md5 digest-md5
sql_engine: mysql
sql_hostnames: localhost
sql_user: postfixadmin
sql_passwd: "password"
sql_database: postfixadmin
sql_select: select password from mailbox where username='%u@%r' and active = 1

```

---


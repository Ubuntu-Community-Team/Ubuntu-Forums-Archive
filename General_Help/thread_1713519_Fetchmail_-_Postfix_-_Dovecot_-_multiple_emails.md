---
title: "Fetchmail - Postfix - Dovecot - multiple emails"
date: 2011-03-24
forum: General Help
---

### Post by ShuckTheFootUp on 2011-03-24
Lads/Ladies

Firstly, sorry if this is in the wrong section or has been posted before. I've been a regular lurker here for a long time and have found an absolute wealth of information here for all my Ubuntu problems, but I can't seem to find a solution to my current problem.

I'm trying to set up an email relay for my team. I've downloaded and installed Ubuntu Server and have ended up putting an Xubuntu front end on it. Our email situation is kind of unique. Essentially there are 5 of us in this team who share 1 team email address provided through a free web email service. At the moment I'm using Thunderbird to pull everything off the web and down to my local machine and monitoring everything on behalf of the team. I want to get away from this.

To do this I installed fetchmail, postfix and dovecot using a great How-to I found on this site. I have managed to get this working and can send and receive emails fine. However I have two problems I'm hoping somebody here might be able to help with. 

Firstly: Fetchmail is configured with the following fetchmailrc file (sanitised for privacy):

```

# Configuration created Fri Mar 18 16:39:41 2011 by fetchmailconf 1.57
set postmaster "postmaster"
set bouncemail
set no spambounce
set softbounce
set properties ""
set daemon 1
poll webmail.freemailprovider.com with proto POP3
       user "AAA" there with password "PASSWORDAAA" is BBB here options fetchall

```Postfix is configured as follows:

Main.cf

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

readme_directory = no

# TLS parameters
smtpd_tls_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
smtpd_tls_key_file=/etc/ssl/private/ssl-cert-snakeoil.key
smtpd_use_tls=yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

mydomain = DOMAINNAME
myhostname = MACHINENAME
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = $mydomain
mydestination = localhost.$mydomain, localhost, $myhostname, $mydomain, $myhostname.$mydomain
mynetworks = 127.0.0.0/8 192.XXX.XXX.0/24
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
inet_protocols = all

smtp_generic_maps = hash:/etc/postfix/generic

home_mailbox = Maildir/



# Postfix configuration to relay e-mail through ISP

relayhost = mail.freemailprovider.com

smtp_sasl_auth_enable = yes

smtp_sasl_password_maps = hash:/etc/postfix/sasl_password

smtp_sasl_security_options =



# Postfix configuration as SMTP server

smtpd_sasl_type = dovecot

smtpd_sasl_path = private/auth-client

smtpd_sasl_local_domain =

smtpd_sasl_security_options = noanonymous

broken_sasl_auth_clients = yes

smtpd_sasl_auth_enable = yes

smtpd_recipient_restrictions = permit_sasl_authenticated,permit_mynetworks,reject_unauth_destination

```/etc/aliases

```

# Indicate who is the root user (probably configured, already)

root:    BBB

# See man 5 aliases for format
postmaster:    root
AAA:    BBB

```Fetchmail logs into the free webmail using the user ID AAA and puts the email into Maildir folder on my local machine. However for some reason that I cannot figure out it puts 2 copies of each mail into the Maildir. The first email is for BBB@localhost and the second is for AAA@localhost. The problem is, there is no user AAA on my machine and the username AAA is actually the name used to log into the free webmail service. Does anybody know why fetchmail is trying to put two copies of each mail onto the system? This is causing other problems in that if I don't put AAA: BBB into the Aliases file, anybody who sends an email to us gets an error stating that one of the recipients was unable to be reached and that the mail was not delivered.

I would really appreciate any help you lads could give on this as it's driving me nuts! :)

Cheers

---


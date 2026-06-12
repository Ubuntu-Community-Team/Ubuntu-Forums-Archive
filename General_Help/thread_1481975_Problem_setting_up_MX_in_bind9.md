---
title: "Problem setting up MX in bind9"
date: 2010-05-13
forum: General Help
---

### Post by talonsnow on 2010-05-13
First off, I am very new to trying to administer a linux server, so please bear with me.

I have setup a dedicated server with LAMP, ruby rails, bind9, postfix, dovecot, sasl, svn, redmine, and roundcube.

Everything seems to work after tinkering with it for a while, except receiving email externally. Am able to send email internally between users (not virtual users just real accounts) and also send it out externally. Also, when a virtual user connects with roundcube, they are able to send mail out just not receive any as well.

I got my DNS all setup and working for multiple domains using virtual hosting with apache2. But the MX part confuses me, and I have a hunch it's whats preventing the incoming mail. It seems all the tutorials use mail. or some variant of to identify there mail server, while I have mine as the same machine as the DNS. So I just set it to the domain name, which figured would resolve to the external ip. No clue if this is correct or not.

here was the first error I got in mail.log regarding this issue:
```
May 13 00:11:33 archit postfix/local[11765]: 0892C41E8CD: to=<ScottJensen@sprystudios.net>, relay=local, delay=0.11, delays=0.03/0.04/0/0.04, dsn=5.1.1, status=bounced (unknown user: "scottjensen")
May 13 00:11:33 archit postfix/cleanup[11764]: 1EF0041E8CF: message-id=<20100513071133.1EF0041E8CF@sprystudios.net>
May 13 00:11:33 archit postfix/qmgr[6486]: 1EF0041E8CF: from=<>, size=2427, nrcpt=1 (queue active)
May 13 00:11:33 archit postfix/bounce[11766]: 0892C41E8CD: sender non-delivery notification: 1EF0041E8CF
May 13 00:11:33 archit postfix/qmgr[6486]: 0892C41E8CD: removed

```

After googling around I assumed the "unknown user: "scottjensen" (which is a virtual user) was because I had my domain name listed in mynetworks in postfix so it was always trying to find users as real ones. After I took it out, and tried again I now get:
```
May 13 00:22:38 archit postfix/smtp[11941]: 92A0441E8CA: host smtp.secureserver.net[216.69.186.201] refused to talk to me: 554-m1pismtp01-010.prod.mesa1.secureserver.net 554 Your access to this mail system has been rejected due to the sending MTA's poor reputation. If you believe that this failure is in error, please contact the intended recipient via alternate means.
May 13 00:22:38 archit postfix/smtp[11941]: 92A0441E8CA: to=<ScottJensen@sprystudios.net>, relay=mailstore1.secureserver.net[72.167.238.201]:25, delay=1.1, delays=0.03/0.04/1/0, dsn=4.0.0, status=deferred (host mailstore1.secureserver.net[72.167.238.201] refused to talk to me: 554-p3pismtp01-011.prod.phx3.secureserver.net 554 Your access to this mail system has been rejected due to the sending MTA's poor reputation. If you believe that this failure is in error, please contact the intended recipient via alternate means.)
May 13 00:23:38 archit dovecot: imap-login: Login: user=<archit@sprystudios.net>, method=PLAIN, rip=127.0.0.1, lip=127.0.0.1, secured

```

after trying to find out more on this is seems it's because I have a poor rating now, thinking I could have a Trojan sending out mail. However, it is just cause over the last 2 days in trying to set it all up, it kept trying to send out messages that failed to deliver as they stayed in queue.

I am convinced I have my MX wrong and stopped at this point not wanting to further aggravate the problem with servers thinking I am spamming.

here is my DNS settings for the domain
```
;
; BIND data file for local loopback interface
;
$TTL    604800
@       IN      SOA     ns.sprystudios.net. business.sprystudios.net. (
                             20         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
@       IN      NS      ns.sprystudios.net.
                NS      ns2.sprystudios.net.
                MX      10 sprystudios.net.
@       IN      A       75.139.181.176
@       IN      AAAA    ::1
ns      IN      A       192.168.0.109
ns2             A       192.168.0.109
www             CNAME   ns.
router          A       192.168.0.1

```

and my postfix main.cf settings
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
smtpd_use_tls = yes
smtpd_tls_session_cache_database = btree:${data_directory}/smtpd_scache
smtp_tls_session_cache_database = btree:${data_directory}/smtp_scache

# See /usr/share/doc/postfix/TLS_README.gz in the postfix-doc package for
# information on enabling SSL in the smtp client.

myhostname = sprystudios.net
alias_maps = hash:/etc/postfix/aliases
alias_database = hash:/etc/postfix/aliases
myorigin = /etc/mailname
mydestination = localhost, localhost.localdomain
relayhost =
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.0]/104 [::1]/128
mailbox_command = procmail -a "$EXTENSION"
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
virtual_mailbox_base = /home/vmail
virtual_uid_maps = static:5000
virtual_gid_maps = static:5000
smtpd_sasl_auth_enable = yes
broken_sasl_auth_clients = yes
smtpd_sasl_authenticated_header = yes
smtpd_recipient_restrictions = permit_mynetworks, permit_sasl_authenticated, reject_unauth_destination
virtual_create_maildirsize = yes
virtual_maildir_extended = yes
proxy_read_maps = $local_recipient_maps $mydestination $virtual_alias_maps $virtual_alias_domains $virtual_mailbox_maps $virtual_mailbox_domains $relay_recipient_maps $relay_domains $canonical_maps $sender_canonical_maps $recipient_canonical_maps $relocated_maps $transport_maps $mynetworks $virtual_mailbox_limit_maps
virtual_transport = dovecot
dovecot_destination_recipient_limit = 1

```

here is a dig info
```
; <<>> DiG 9.6.1-P2 <<>> sprystudios.net
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 63740
;; flags: qr rd ra; QUERY: 1, ANSWER: 1, AUTHORITY: 2, ADDITIONAL: 0

;; QUESTION SECTION:
;sprystudios.net.               IN      A

;; ANSWER SECTION:
sprystudios.net.        3600    IN      A       64.202.189.170

;; AUTHORITY SECTION:
sprystudios.net.        1706    IN      NS      ns34.domaincontrol.com.
sprystudios.net.        1706    IN      NS      ns33.domaincontrol.com.

;; Query time: 118 msec
;; SERVER: 192.168.0.1#53(192.168.0.1)
;; WHEN: Thu May 13 01:58:28 2010
;; MSG SIZE  rcvd: 104

```

Any help would be greatly appreciated!

---


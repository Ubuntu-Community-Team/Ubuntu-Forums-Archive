---
title: "postfix configuration"
date: 2012-08-27
forum: General Help
---

### Post by ludo1960 on 2012-08-27
Hello,

Followed this tutorial [http://www.debiansystemadmin.com/con...-squirrelmail/]("http://www.debiansystemadmin.com/configuring-postfix-mail-server-with-sasl-dovecot-and-squirrelmail/") and set up my debian box.

I can send mail from the server, but seem to have issues receiving mail: Here's the tail end of the log file:

Aug 27 11:39:57 myserver dovecot: auth-worker(default): pam(info,127.0.0.1): lookup service=dovecot
Aug 27 11:39:57 myserver dovecot: auth-worker(default): pam(info,127.0.0.1): #1/1 style=1 msg=Password: 
Aug 27 11:39:57 myserver dovecot: auth(default): client out: OK#0111#011user=info
Aug 27 11:39:57 myserver dovecot: auth(default): master in: REQUEST#01136#01124779#0111
Aug 27 11:39:57 myserver dovecot: auth(default): passwd(info,127.0.0.1): lookup
Aug 27 11:39:57 myserver dovecot: auth(default): master out:  USER#01136#011info#011system_groups_user=info#011uid=1001#011gid=100#011home=/home/info
Aug 27 11:39:57 myserver dovecot: imap-login: Login: user=<info>, method=PLAIN, rip=127.0.0.1, lip=127.0.0.1, secured
Aug 27 11:39:57 myserver dovecot: IMAP(info): Effective uid=1001, gid=100, home=/home/info
Aug 27 11:39:57 myserver dovecot: IMAP(info): maildir: data=~/Maildir
Aug 27 11:39:57 myserver dovecot: IMAP(info): maildir++: root=/home/info/Maildir, index=, control=, inbox=/home/info/Maildir
Aug 27 11:39:57 myserver dovecot: IMAP(info): Namespace : Using permissions from /home/info/Maildir: mode=0700 gid=-1
Aug 27 11:39:57 myserver dovecot: IMAP(info): Disconnected: Logged out bytes=85/681
Aug 27 11:39:58 myserver dovecot: auth(default): new auth connection: pid=26057
Aug 27 11:39:58 myserver dovecot: auth(default2): new auth connection: pid=26057

And here's my main.cf

# See /usr/share/postfix/main.cf.dist for a commented, more complete version


# Debian specific:  Specifying a file name will cause the first
# line of that file to be used as the name.  The Debian default
# is /etc/mailname.
#myorigin = /etc/mailname

smtpd_banner = $myhostname ESMTP $mail_name (Debian/GNU)
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

myhostname = mysite.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = /etc/mailname
mydestination = mysite.com, localhost.com, , localhost
relayhost = 
mynetworks = 127.0.0.0/8 [::ffff:127.0.0.1]/104 [::1]/128.10.0.0.0/24
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
mailbox_command = procmail
home_mailbox = Maildir/

smtpd_sasl_type = dovecot
smtpd_sasl_path = private/auth
smtpd_sasl_auth_enable = yes
smtpd_sasl_local_domain = tcs.local
smtpd_recippient_restrictions = permit_mynetworks,permit_sasl_authenticated,reject_unauth_destination
Smtpd_sasl_security_options = noanonymous

I also installed procmail as the system complained it couldn't find it.  Any ideas guys, it's quite tricky to set up a mail server, for me  anyhow!

---

### Post by neur0 on 2012-08-27
My suggestion is that you first check that email is routed to the server in the first place. 
Check the sending server's logs for errors if you have access. If not, see if your mail gets returned.
Check the mail log for incomming mail and see if the mail is being put in the mailbox/maildir.
If all this seems OK, then you, most likely, have a problem with Dovecot or the mail client.

In short: reverse your troubleshooting. Start with:
Is mail reaching my server? [DNS, IPtables etc]
Is it being delivered in the apropriate inbox? [MTA/MDA]
Can I retreive it from the inbox using POP3/IMAP? [MDA/MUA]

If you have problems with specifics, feel free to ask.

---

### Post by ludo1960 on 2012-08-27
Thanks for reply,

Start at the beginning: Is mail reaching my server? [DNS, IPtables etc] ? how do I test that?

Apologies for my ignorance, way out my depth with e-mail server stuff

Thank you again for input.

---

### Post by neur0 on 2012-08-28
Without any detailed info, I would do something like this from a client computer (not server):

Check if there is an MX record for the domain that points to your server:

```
host -t MX domain.com
```

Replace domain.com with your domain ofc.

Than, if you get something like mail.domain.com, check if it has a correct HOST record with:

```
host mail.domain.com
```

Replace mail.domain.com with the MX record found by the previous command.

The IP address should match the IP address of your server.

That's the DNS part.

Next, try to telnet to the server:

```
telnet mail.domain.com 25
```

If you get a prompt, type:

```
EHLO localhost
```

I you get some info and not an error, Postfix is listening to incomming connections and everything is fine with the network layer.


If you can't telnet to the server on port 25, check if postfix is listening for incomming connections. On the server type:

```
netstat -nltp
```

There should be a line that looks something like this:
```
tcp  0  0  0.0.0.0:25  0.0.0.0:*  LISTEN  890/master
```

Instead of "master", there may be some other name like "postfix" Look for the port number (:25) if in doubt. Instead of "0.0.0.0" you may be using your public IP address, thes also OK. 
Also there will probably be another similar line with ":::25" in the address field. That's IPV6, and you can ignore it for now.

If there is nothing listening on port 25, you should check if postfix is started:

```
sudo service postfix status
```

If this is all OK, check IPtables to make sure you aren't blocking mail traffic on the server:

```
sudo iptables -L
```

Note the "Chain INPUT"
If in doubt, paste the output here, but mask any IP adresses or other personal info.

If this is all OK, send a mail to a local user from a remote client (or any webmail) and check the server log for errors.

Report your findings so we can investigate further.

---

### Post by ludo1960 on 2012-09-14
AHA, seems after checking the various error logs that apache (default install) is not  correctly configured as all requests are sent to /var/www so other processes never gets called! So the question now is how to  change the apache config?

---


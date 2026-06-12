---
title: "Postfix (slightly) open relay"
date: 2006-03-08
forum: General Help
---

### Post by stocksy on 2006-03-08
I've been trying to set postfix up to act as a backup mail server.  I tested it using the tools at ordb.org, and it reported that it does not appear to be an open relay.  When I checked the logs, however, I found a couple of lines like this:

```

Feb 28 18:33:38 mail2 postfix/smtp[21592]: 03FA457EED: to=<xxx@yyy.gov.tw>, relay=smssmtp93.yyy.gov.tw[xxx.29.159.xx], delay=15, status=sent (250 M2006030102441004449 Message accepted for delivery)
Mar  1 13:05:21 mail2 postfix/smtp[2707]: 2B26557EE4: to=<xxx@yyy.com>, relay=mail.yyy.com[xxx.114.216.xxx], delay=147106, status=sent (250 2.0.0 k21D5aMO014409 Message accepted for delivery)

```

When I saw this, I shut down postfix right away, but I can't see how this is happening.  Here's my config:

main.cf:

```

smtpd_banner = $myhostname ESMTP $mail_name (Ubuntu)
biff = no
append_dot_mydomain = no
inet_interfaces = all
relay_domains = hash:/etc/postfix/relays
transport_maps = hash:/etc/postfix/transport
smtpd_recipient_restrictions = check_relay_domains

```

relays:

```

my.domain.tld OK

```

transport:

```

my.domain.tld smtp:mail.my.domain.tld

```

Can anyone see the problem?

---

### Post by stocksy on 2006-03-09
I'll give this just one bump.

---

### Post by lamego on 2006-03-09
Are you sure this mails are not local ?
The log messages show hat those emails have been delivered from to remote relays (which is just as any normap email client works) they  don't indicate that your system is relaying anything...

---

### Post by stocksy on 2006-03-12
[QUOTE=lamego]Are you sure this mails are not local ?[/QUOTE]

Thanks for your reply.  I think it's unlikely to be local sender. All the other computers on the LAN are OS X Macs and I trust all the users.  Indeed, if I try to connect to it from the LAN and send outgoing mail it declines to relay it!

```

$ telnet 192.168.0.222 25
Trying 192.168.0.222...
Connected to 192.168.0.222.
Escape character is '^]'.
220 yyy.xxx.net ESMTP Postfix (Ubuntu)
ehlo emac.local
250-yyy.xxx.net
250-PIPELINING
250-SIZE 10240000
250-VRFY
250-ETRN
250 8BITMIME
mail from:<test@test.test>
250 Ok
rcpt to:<stocksy@gmail.com>
554 <stocksy@gmail.com>: Recipient address rejected: Relay access denied
rcpt to:<foo@bar.tld>
554 <foo@bar.tld>: Recipient address rejected: Relay access denied
quit
221 Bye
Connection closed by foreign host.

```

AFAIK, my postfix install just considers 127.0.0.1 to be local.  I just don't understand how these emails can be getting through.

---

### Post by stocksy on 2006-03-15
Well, this turned out to be a clear cut case of PEBKAC.  I was simply grepping the mail.log for lines containing status=sent, but not containing @stocksy.co.uk.  Simple no?  Well, I needed to look at the whole story:
```

Mar 10 06:45:09 mail2 postfix/smtpd[27979]: connect from unknown[xxx.xxx.202.132] 
Mar 10 06:45:10 mail2 postfix/smtpd[27979]: warning: support for restriction "check_relay_domains" will be removed from Postfix; use "reject_unauth_destination" instead 
Mar 10 06:45:10 mail2 postfix/smtpd[27979]: warning: restriction `reject_unauth_destination' after `check_relay_domains' is ignored 
Mar 10 06:45:10 mail2 postfix/smtpd[27979]: E3BF157EA1: client=unknown[xxx.xxx.202.132] 
Mar 10 06:45:11 mail2 postfix/cleanup[27983]: E3BF157EA1: message-id=<000001c6440e$3d624880$02cfa8c0@ybb62> 
Mar 10 06:45:11 mail2 postfix/qmgr[21151]: E3BF157EA1: from=<beulahhir@xxxxxx.or.jp>, size=3451, nrcpt=1 (queue active) 
Mar 10 06:45:12 mail2 postfix/smtpd[27979]: disconnect from unknown[xxx.xxx.202.132] 
Mar 10 06:45:13 mail2 postfix/smtp[27984]: E3BF157EA1: to=<eepolito@stocksy.co.uk>, relay=mail.toastputer.net[69.93.127.12], delay=3, status=bounced (host mail.toastputer.net[69.93.127.12] said: 550 <eepolito@stocksy.co.uk>: Recipient address rejected: User unknown in virtual mailbox table (in reply to RCPT TO command)) 
Mar 10 06:45:13 mail2 postfix/cleanup[27983]: E1B5A57ED7: message-id=<20060310064513.E1B5A57ED7@mail2.toastputer.net> 
Mar 10 06:45:13 mail2 postfix/qmgr[21151]: E3BF157EA1: removed 
Mar 10 06:45:13 mail2 postfix/qmgr[21151]: E1B5A57ED7: from=<>, size=5454, nrcpt=1 (queue active) 
Mar 10 06:45:28 mail2 postfix/smtp[27984]: E1B5A57ED7: to=<beulahhir@xxxxxx.or.jp>, relay=mailgw1.xxxxxx.or.jp[xxx.xxx.106.55], delay=15, status=sent (250 ok 1141973167 qp 27149) 
Mar 10 06:45:28 mail2 postfix/qmgr[21151]: E1B5A57ED7: removed 

```
I had failed to account for bounce messages.  This is just somebody trying to spam the non-existant 'eepolito' address, which my backup MX accepts because it is a relay domain.  My primary MX, however, refuses to accept the message because it is not a valid user, so my backup MX bounces it back to the sender - hence the status=sent line.

/me smacks his forehead!

---


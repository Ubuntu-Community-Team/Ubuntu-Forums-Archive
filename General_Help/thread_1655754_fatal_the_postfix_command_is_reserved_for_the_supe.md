---
title: "fatal: the postfix command is reserved for the superuser"
date: 2010-12-30
forum: General Help
---

### Post by Dimas on 2010-12-30
Hi!

I've made a real mistake... While I'm trying to change the owner of a /var/www/example/var I've changed all the /var content (_chown www-data /var_ instead of _chown www-data var_ :(). I tried executing _chown root /var_, but now I have problems with Postfix...

In my webpages I use different commands to send mails:
- The *phpMailer* class
- The *mail()* command

The phpmailer is working, but not mail() :(

When I try *mail()* I've these messages in /var/log/mail.log:

```
Dec 30 09:42:31 zeus postfix[3829]: error: to submit mail, use the Postfix sendmail command
Dec 30 09:42:31 zeus postfix[3829]: fatal: the postfix command is reserved for the superuser
```Terminal *mail* command is not working either.

In my /etc/php5/apache2/php.ini I've this configuration:

```

[mail function]
; For Win32 only.
; [http://php.net/smtp](http://php.net/smtp)
;SMTP = localhost
; [http://php.net/smtp-port](http://php.net/smtp-port)
;smtp_port = 25
; For Win32 only.
; [http://php.net/sendmail-from](http://php.net/sendmail-from)
;sendmail_from = [EMAIL="dstreich.girona.ics@gencat.cat"]dstreich.girona.ics@gencat.cat[/EMAIL]
; For Unix only.  You may supply arguments as well (default: "sendmail -t -i").
; [http://php.net/sendmail-path](http://php.net/sendmail-path)
sendmail_path = /usr/sbin/postfix

```

I also tried sendmail -t -i without luck.

Can you help me? :confused:

---

### Post by dcstar on 2010-12-31
> **Dimas said:**
> Hi!

I've made a real mistake... While I'm trying to change the owner of a /var/www/example/var I've changed all the /var content (_chown www-data /var_ instead of _chown www-data var_ :(). I tried executing _chown root /var_, but now I have problems with Postfix...
..........:

**You** have damaged a system folder. Reinstall the postfix package and it might work again.

---

### Post by Dimas on 2011-01-09
It didn't worked :(

---


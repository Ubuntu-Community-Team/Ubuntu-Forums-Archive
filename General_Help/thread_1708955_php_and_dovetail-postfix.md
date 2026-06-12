---
title: "php and dovetail-postfix"
date: 2011-03-17
forum: General Help
---

### Post by Pacopag on 2011-03-17
Hi.  I'm having a heck of a time getting php's mail() function to work.  I don't get any errors when I use it, but the mail just isn't arriving where it should.

The folks in the PHP forums have helped all they can, so I thought I'd ask here.

So far, I've installed php5,apache2,mysql.  Everything there works fine.  Then the PHP guys told me to install dovecot-postfix as a mail server.  So I did that. PHP mail() still does nothing.  I don't know what else to do, except to post the relevant part of php.ini

[mail function]
; For Win32 only.
; [http://php.net/smtp](http://php.net/smtp)
 SMTP = localhost
; [http://php.net/smtp-port](http://php.net/smtp-port)
 smtp_port = 25

; For Win32 only.
; [http://php.net/sendmail-from](http://php.net/sendmail-from)
; sendmail_from = [email]misswwwcanada@gmail.com[/email]

; For Unix only.  You may supply arguments as well (default: "sendmail -t -i").
; [http://php.net/sendmail-path](http://php.net/sendmail-path)
 sendmail_path = /usr/sbin/sendmail -t -i

I think that's it.

I actually had mail() working at the office yesterday by following this link
[http://mattsk.blogspot.com/2010/09/configure-lamp-on-ubuntu-1004-to-send.html](http://mattsk.blogspot.com/2010/09/configure-lamp-on-ubuntu-1004-to-send.html)
But it doesn't work at home today.  Strange.  I thought it was my firewall, but I turned it off an mail() still doesn't work.

Any help would be great.

Oh....and "dovetail" in the title of this post should be "dovecot".  Sorry,  spring is nearby, and the doves have returned where I live, so I guess I've got the birds on my mind.

---


---
title: "Problem with sending mail via smtp.gmail ( php )"
date: 2011-02-25
forum: General Help
---

### Post by AndrejKrnac on 2011-02-25
HI ,
I want to send mails via gmail with php. I need to know how to configure main.cf, php.ini, postfix,smtp... and all what is necessary. I tried a lot but no results.
Please try explain it me throught  easy way. Or give me tutorials for it.
Thanks a lot.

---

### Post by LoneWolfJack on 2011-02-25
[http://www.thelampblog.com/2010/11/07/php-send-mail-via-smtp/]("http://www.thelampblog.com/2010/11/07/php-send-mail-via-smtp/")

(not my blog)

---

### Post by wiggly81 on 2011-02-25
```
		
$mail_host = "mail.yoursite.com";
$mail_port = "25";
$mail_addy = "me@mysite.com";
ini_set("SMTP", $mail_host);
ini_set("SMTP_PORT", $mail_port);
ini_set("sendmail_from", $mail_addy);

```

add that to you php file it works on my sites

---

### Post by AndrejKrnac on 2011-02-28
> **wiggly81 said:**
> ```
        
$mail_host = "mail.yoursite.com";
$mail_port = "25";
$mail_addy = "me@mysite.com";
ini_set("SMTP", $mail_host);
ini_set("SMTP_PORT", $mail_port);
ini_set("sendmail_from", $mail_addy);

```add that to you php file it works on my sites

It is not a configuration of Postfix, or main.cf,....I think at first a have to configurate..

now in my mail.log reloads every minute this error:

Feb 28 17:20:16 Andrej postfix/qmgr[4299]: fatal: dict_open: unsupported dictionary type: ssl:  Is the postfix-ssl package installed?
Feb 28 17:20:16 Andrej postfix/pickup[4298]: fatal: dict_open: unsupported dictionary type: ssl:  Is the postfix-ssl package installed?
Feb 28 17:20:17 Andrej postfix/master[2943]: warning: process /usr/lib/postfix/qmgr pid 4299 exit status 1
Feb 28 17:20:17 Andrej postfix/master[2943]: warning: /usr/lib/postfix/qmgr: bad command startup -- throttling
Feb 28 17:20:17 Andrej postfix/master[2943]: warning: process /usr/lib/postfix/pickup pid 4298 exit status 1
Feb 28 17:20:17 Andrej postfix/master[2943]: warning: /usr/lib/postfix/pickup: bad command startup -- throttling


Can you help me ?

---

### Post by AndrejKrnac on 2011-02-28
> **LoneWolfJack said:**
> [http://www.thelampblog.com/2010/11/07/php-send-mail-via-smtp/](http://www.thelampblog.com/2010/11/07/php-send-mail-via-smtp/)

(not my blog)

I do not need script to send mail....I think at first I need configurate smtp or postfix or....I do not know...

I write below my errors in mail.log.....can you help me ?

---

### Post by LoneWolfJack on 2011-02-28
as the error message states, you are probably trying to send mail from a script that is being run in a SSL context. you can't do that without first installing postfix-ssl.

that aside, you can only get away with abusing mail() by forcing it to send mail through a SMTP server as long as the server doesn't require authentication.

if it does, you will have to use one of the various PHP sendmail classes or implement your own. Craig's blog post provides the basics for doing that.

/edit
shouldn't a mod move this thing to programming talk?

---


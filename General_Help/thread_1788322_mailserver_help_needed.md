---
title: "mailserver help needed"
date: 2011-06-22
forum: General Help
---

### Post by YIFY on 2011-06-22
Hi I am not sure if this is the right place to post asking for a bit of help but ill try anyways.

I have been trying to set up a mail server on my VPS running buntu 10.04.2 LTS (32bit)

I am using MTA postfix mail server. but after lots of configuring I still get all the mail sent going to spam on both hotmail and gmail. here is my set-up and configs:




[LIST]
[*] I have my own my domain-name (lets call it mycooldomain.com)
[/LIST]


[LIST]
[*]the reverse-DSN for my VPS IP  is pointing to "mail.mycooldomain.com."
[/LIST]


[LIST]
[*]MX DNS Record:  VPS IP points to "mail.mycooldomain.com" at priority=10
[/LIST]


[LIST]
[*]VPS hostname: "mail.mycooldomain.com"
[/LIST]


[LIST]
[*]Contect of the hosts file (/etc/hosts):
[/LIST]
127.0.0.1 localhost.localdomain localhost mail.mycooldomain.com
# Auto-generated hostname. Please do not remove this comment.
174.456.245.223 mail.mycooldomain.com  mail
```

```



[LIST]
[*]my postfix config file:
[/LIST]

```
smtpd_banner = $myhostname ESMTP $mail_name
biff = no

# appending .domain is the MUA's job.
append_dot_mydomain = no

# Uncomment the next line to generate "delayed mail" warnings
#delay_warning_time = 4h



myhostname = mycooldomain.com
alias_maps = hash:/etc/aliases
alias_database = hash:/etc/aliases
myorigin = mycooldomain.com
mydestination = $mycooldomain.com, localhost.$mycooldomain.com, , localhost
relayhost =
mynetworks = 127.0.0.0/8
mailbox_command = procmail -a "$EXTENSION"
mailbox_size_limit = 0
recipient_delimiter = +
inet_interfaces = all
html_directory = /usr/share/doc/postfix/html
```


Any help to configure this correctly to to send out emails that end in spam, will be more then greatly appreciated!

---

### Post by YIFY on 2011-06-22
UPDATE:

When I put in the postfix config:

```
myorigin = $mydomain
```

instead of the original:

```
myorigin = mycooldomain.com
```

the emails DONT go to spam but the sender details are "root@com" and I want them to be "root@mycooldomain.com"

---

### Post by Habitual on 2011-06-22
Edit: burp

---


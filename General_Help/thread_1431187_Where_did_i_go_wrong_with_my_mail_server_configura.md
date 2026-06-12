---
title: "Where did i go wrong with my mail server configuration"
date: 2010-03-16
forum: General Help
---

### Post by stjohnmedrano on 2010-03-16
> Queue ID- --Size-- ----Arrival Time---- -Sender/Recipient-------
EB0DF409F9      417 Tue Mar 16 20:49:07  [EMAIL="mymail@example.com"]mymail@example.com[/EMAIL]
        (connect to aspmx2.googlemail.com[209.85.135.27]:25: No route to host)
                                         [EMAIL="yourmail@hismail.com"]yourmail@hismail.com[/EMAIL]
(connect to alt4.gmail-smtp-in.l.google.com[209.85.219.47]:25: No route to host)
                                         [EMAIL="yourmail@gmail.com"]yourmail@gmail.com[/EMAIL]
good evening im trying to make a personal mail server my problem is i cant send (outbound mails)

i just edited some of the mail address..

where did i get wrong?  thank you so much...

---

### Post by stjohnmedrano on 2010-03-16
and ive also try connecting tru my telnet [email]mymail@server.com[/email] 25

unable to connect to remote host.

thank you so much.

---

### Post by dcstar on 2010-03-17
> **stjohnmedrano said:**
> good evening im trying to make a personal mail server my problem is i cant send (outbound mails)
```
Queue ID- --Size-- ----Arrival Time---- -Sender/Recipient-------
EB0DF409F9 417 Tue Mar 16 20:49:07 mymail@example.com
(connect to aspmx2.googlemail.com[209.85.135.27]:25: No route to host)
yourmail@hismail.com
(connect to alt4.gmail-smtp-in.l.google.com[209.85.219.47**:25**: No route to host)
yourmail@gmail.com
```
i just edited some of the mail address..

where did i get wrong?  thank you so much...

Please do not "quote" code - use the CODE tag.

Get rid of the **:25** you put in.

---

### Post by amauk on 2010-03-17
as far as I know,
google's relay servers run on port 587 (using TLS)
not 25 (which is unencrypted)

---


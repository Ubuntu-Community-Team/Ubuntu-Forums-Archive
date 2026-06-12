---
title: "Unable to send mail using evolution"
date: 2009-09-10
forum: General Help
---

### Post by lithops on 2009-09-10
I have just installed ubuntu using wubi and the process has been very successful. I am able to receive e-mail with evolution with no problem but cannot receive. The message, after entering my password, is "unable to authenticate to smtp server; bad authentication response from server"

The settings I am using are the same as those used for Thunderbird in Windows XP and that has worked fine for months.

I have rechecked the settings.

Any suggestions as to my next step.

Thank you,

lithops

---

### Post by nigj on 2009-09-11
Hi
try finding settings for sending (uess u have an pop account) and add a : and then the port ur supposed to use. mail.c2i.net:587 guess this will help u

---

### Post by brettg on 2009-09-11
Assuming that you are just using your isp mail server then you should be aware that usually authentication is NOT required for smtp.

Make sure you check that "Server requires authentication" is unchecked in Evolution preferences.

---

### Post by lithops on 2009-09-11
My isp does require authentication so I have checked the authentication box. The outgoing server is smtpauth.fairpoint.net.

Does that tell anybody anything

All the best,
lithops

---

### Post by brettg on 2009-09-13
Are you sure that they require authentication for smtp? They usually require it for pop3 but not smtp.

Try connecting via telnet to the server

telnet smtp.example.com 25

You should see something akin to;

Trying n.n.n.n...
Connected to smtp.example.com.
Escape character is '^]'.
220 smtp.example.com ESMTP Exim 4.69 Mon, 14 Sep 2009 18:25:24 +1000

---


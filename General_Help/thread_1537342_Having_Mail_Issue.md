---
title: "Having Mail Issue"
date: 2010-07-23
forum: General Help
---

### Post by Belgin Fish on 2010-07-23
Hi,

I'm trying to get mail working on my ubuntu server, for the smtp server i just put the ip, i don't believe I have any auth setup.

Now it's telling me

 Unable to connect to mail server: Connection refused(111)

Does anyone have any idea whats going on? :(

Thanks

---

### Post by Zill on 2010-07-23
Belgin Fish:  Are you running your own mail server or a mail client such as Evolution?

Some mail servers *do* require authentication to help prevent misuse.

If you are running Evolution then you could try setting the "Server requires authentication" box and entering your mail username in the smtp authentication field.  If you also check the "Remember password" box then the first time you connect it will ask for your password once and that will be it!

ps.  Make sure your server configuration is actually pointing to a "real" mailserver. eg. smtp.myisp.net. This info should have been supplied by your ISP.

---

### Post by Belgin Fish on 2010-07-23
Thanks, hopefully I'll be able to get it worked out :)

---

### Post by dcstar on 2010-07-24
> **Belgin Fish said:**
> Hi,

I'm trying to get mail working on my ubuntu server, for the smtp server i just put the ip, i don't believe I have any auth setup.

Now it's telling me

 Unable to connect to mail server: Connection refused(111)

Does anyone have any idea whats going on? :(

Thanks

What MTA did you install?

---

### Post by Belgin Fish on 2010-07-24
I don't even think I installed one to be honest lol

---


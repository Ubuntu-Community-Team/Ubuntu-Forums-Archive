---
title: "Multiple ip-based hosts on Ubuntu and php mail"
date: 2011-02-21
forum: General Help
---

### Post by jelo77 on 2011-02-21
Hi,

I have two IP based hosts on an Ubuntu server with Apache 2.2 and php. When I send email through php (mail function), the headers from both hosts show the same information at the email recipient, e.g.

Received: from machine name.domain (hostname [IP addess])

However, I believe the headers should correctly show from which host the message came and not be the same for both hosts, right? The correct setting should be something like this:

Received: from machine name.domain (hostname1 [IP addess1])
vs.
Received: from machine name.domain (hostname2 [IP addess2])

What setting influences this behaviour? Is it a Ubuntu setting, Apache server setting, mail server setting, php configuration?

Thanks, J.

---

### Post by Habitual on 2011-02-21
What MTA are you using?

---

### Post by jelo77 on 2011-02-21
Thanks for the quick reply. Sendmail to my knowledge, but I will make sure tomorrow...

---


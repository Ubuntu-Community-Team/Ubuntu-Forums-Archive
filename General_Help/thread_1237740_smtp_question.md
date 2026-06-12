---
title: "smtp question"
date: 2009-08-11
forum: General Help
---

### Post by Matsaki on 2009-08-11
I have a server with Ubuntu 8.04.2 and using it for my community and other sites I have. I use Postfix for email verification and email handling.

No I wonder if there is a good tutorial how I can configure Postfix so I can use my server for my own emails from my computer as I now use my computers own localhost or my ISP's SMTP.

I.e I want to use smtp.mydomain.com as SMTP. I am not very familiar with Ubuntu and as the server is in another Country I have to use SSH to configure Ubuntu modules.

Thanks!

---

### Post by jonobr on 2009-08-11
coming at this question from a different angle,

You need to ensure your ISP allows SMTP, a large amount of them do not and block it as systems could end up being used as mail relays.

On the actual howto there is [This]("https://help.ubuntu.com/community/Postfix")
Im not sure if it helps as I have not tried it

---


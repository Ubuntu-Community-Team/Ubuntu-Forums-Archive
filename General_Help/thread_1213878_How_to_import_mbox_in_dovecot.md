---
title: "How to import mbox in dovecot"
date: 2009-07-15
forum: General Help
---

### Post by Eniac on 2009-07-15
Hi all,

first, im relatively new to ubuntu. I've converted my pc and server from MS to ubuntu about a month ago and i must say i love it.

I'm still pretty new to the internal workings of ubuntu, bash commands and all that.

but thanks to online help, ive been able to setup my internal imap mail server with dovecot, fetchmail and postfix. it works just fine.

but now im trying to import my old mail in Thunderbird into my dovecot (imap) inbox on the server. and im not quite sure if i can just take TB's inbox and copy it right on the server or use another method.

any suggestions ?

---

### Post by HermanAB on 2009-07-15
Click drag drop - seriously!

Simply create multiple accounts in Thunderbird pointing to the old MBOX mail (maybe a dummy mail.example.com account) and the new mail on the server, then select and click drag drop the mail from the one to the other.

You could also copy the MBOX file to the server and use formail (from the fetchmail package) to accomplish the same, with much more effort.

---


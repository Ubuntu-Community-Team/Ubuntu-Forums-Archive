---
title: "postfix question"
date: 2010-03-22
forum: General Help
---

### Post by evaristegalois on 2010-03-22
I just set up mutt for the first time, I am quite proud to have gotten it to work (took me about a week). I used to use thunderbird and evolution, but I love that mutt is all terminal and keyboard. In any case, a lot of my messages that I am sending are being rejected by the recipient's mail server. This is not entirely surprising -- I didn't set up any outgoing mail options (and postfix is sending off my messages, right?), and in thunderbird I used to have to specify shawmail.cg.shawcable.net (shaw is my internet provider) to send messages, not my own server mail.mydomainname.com. In fact, I don't even know what outgoing server postfix uses to send off my messages. My test emails sent from mutt all worked right away, but the problem remains that some recipients want the added safety to know that my messages come from an approved mail server.

So, how do I make sure that shawmail.cg.shawcable.net is my outgoing mail server?

---

### Post by evaristegalois on 2010-03-22
This appears to answer my own question. I just tested it, and it looks promising:

[http://www.mail-abuse.com/an_rteoutgoing.html](http://www.mail-abuse.com/an_rteoutgoing.html)

---


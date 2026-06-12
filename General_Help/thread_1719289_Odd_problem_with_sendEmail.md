---
title: "Odd problem with sendEmail"
date: 2011-04-01
forum: General Help
---

### Post by clustro on 2011-04-01
Hi there,

First time poster here. I have an issue with sendEmail.

I am running Ubuntu 10.04.2 on a Dell Optiplex 380.

Here is the command I am using:

sendEmail -f [EMAIL="X@gmail.com"]X@gmail.com[/EMAIL] -t [EMAIL="Y@gmail.com"]Y@gmail.com[/EMAIL] -m "This is an SMS message from Linux." -o tls=yes -s smtp.gmail.com -xu ZZZ -xp ZZZ

(obviously, some censoring has been done)

The problem is that I try to send emails, I get back that they have been successfully sent, but they do not appear in [EMAIL="Y@gmail.com"]Y@gmail.com[/EMAIL]. When I log in to [EMAIL="X@gmail.com"]X@gmail.com[/EMAIL], the messages *are* in the sent items bin, and are being directed to Y. I thought they might be getting caught as spam, but I tried searching Y (in the search bar at the top) and couldn't find anything.

The kicker is that, by setting tls=auto, I can text message myself using gmail. So gmail is at least working on that front.

Any help is appreciated,

-clustro

---


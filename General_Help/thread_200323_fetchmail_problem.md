---
title: "fetchmail problem"
date: 2006-06-20
forum: General Help
---

### Post by jethro10 on 2006-06-20
Hi,
There seems to be tons of simple pop collectors for windows, mostly used for MS exchange where the program collects pop mail from a server and sends it to your internal smtp server port. Effectivley allowing you to keep your internal mail server behind your firewall.

On linux the closest i've found is fetchmail. I've sorta got it running, it collects mail but sends it all to "jeff@localhost" jeff being the logged on usersname.

All I want to do is use fetchmail as a passthrough like the MS programs above to collect mail from a multidrop box on the internet and let the internal mail server sort it as necessary. It seems as if it may be an envelope option is needed but can I hell as like, get it to work.
Can anyone advise how I can use fetchmail (or similar?) to just be a pop collector and straightforward passthrough so when the collection picks [email]jeff@mydomain.com[/email], it passes it through as [email]jeff@mydomain.com[/email] with no interference.

Jeff

---

### Post by linuchsan on 2006-06-20
poll smtp.your.isp proto pop3 user "XXXXX" password "XXXXX" is "naam@local.smtp.server" here

---

### Post by jethro10 on 2006-06-20
[QUOTE=linuchsan]poll smtp.your.isp proto pop3 user "XXXXX" password "XXXXX" is "naam@local.smtp.server" here[/QUOTE]

But does this not re-write the too address? making it "naam@local.smtp.server" for every user?

what I was after was transparent passthrough so :=

[email]a@myserver.com[/email] = [email]a@myserver.com[/email]
[email]b@myserver.com[/email] = [email]b@myserver.com[/email]

etc.

Jeff

---

### Post by linuchsan on 2006-06-20
I don't know what your local mail-server setup is.
But for every pop account you have to send it to the right local recipient

poll smtp.your.isp proto pop3 user "jeff" password "blabla" is "jeff@local.smtp.server" here
poll smtp.your.isp proto pop3 user "john" password "blabla" is "john@local.smtp.server" here
etc.

---

### Post by jethro10 on 2006-06-20
[QUOTE=linuchsan]I don't know what your local mail-server setup is.
But for every pop account you have to send it to the right local recipient

poll smtp.your.isp proto pop3 user "jeff" password "blabla" is "jeff@local.smtp.server" here
poll smtp.your.isp proto pop3 user "john" password "blabla" is "john@local.smtp.server" here
etc.[/QUOTE]
I see, I need an entry for each user, this adds to the administration
I was rather hoping the fetchmail would just pass everything though transparently to the internal smtp server and let the real mail server decide what to do with each one.
Thanks anyway
Jeff

---

### Post by linuchsan on 2006-06-20
Yes you can with a smtpd proxy, but you still need to empty the mail boxes.

---

### Post by jethro10 on 2006-06-20
[QUOTE=linuchsan]Yes you can with a smtpd proxy, but you still need to empty the mail boxes.[/QUOTE]

this bits getting too complicatesd for me, I think i'll use a windows product on one of my windows servers. I can get one for $100 and it takes 2 minutes to setup  and i've spent more than that on the time i've been playing around with this.

wow

Jeff

---


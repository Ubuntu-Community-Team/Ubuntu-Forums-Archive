---
title: "POSTFIX grasp how the system works"
date: 2010-08-03
forum: General Help
---

### Post by MartinusEx on 2010-08-03
Hi folks,

this thread has following purposes:
1. when I state my problems i better understand them, hence probably come to a solution on my own

2. if I cannot resolve a problem, some of you might be able to help

3. This thread doesn't ask for a "how to", rather than a "It principally should work a certain way"

OK

I run some PC an a small network in a peer to peer fashion (file sharing etc.) not a server client one.

With two of them I try to establish a local mail system (purely local, a true mail server is in sight, but that will follow later on, when I understand this)

On PC "A",  i installed postfix
(assuming i did the configuration correctly)

Now I want to send a mail via "Mail" or"sendmail" to a user account at PC "B".

That doesn't work

Assuming that I need postfix on PC "B" as well I installed it there too (Configured it with the necessary changes)

Still nothing in both directions.

I'm sure that I lack understanding of the system, but I don't grasp it.

mail responds always with bounced mails

1. If I view both PC's as mail servers, they somehow should communicate.
But how do they do that if ever

2.If I have PC "A" being the only mail server, how does the mail command (from mailutils) on PC "B" know how to contact postfix on PC "A" as  a client.

So far I didn't reveal anything new to myself, so I still need to rely on you.

thx in advance

Martin

---


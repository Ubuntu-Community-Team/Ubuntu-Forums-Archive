---
title: "Postfix SMTP forwarding"
date: 2009-09-06
forum: General Help
---

### Post by STRYK3R on 2009-09-06
I am really new to linux and have very little understanding, i have a problem with Microsoft exchange 2003 and i think Linux may be able to help with a solution. First i will start with the problem, I am running a small microsoft exchange 2003 server with roughly 25 members on it using pytheas as the mailer, i ran an update recently and now when a user of the exchange server sends a mail to another person on exchange it goes direct internally instead of going out to our ISP provider and returning. This is causing people to moan that when they check there external webmail at home they do not see the emails that were sent from the exchanges users. 
 
Now i understand that Postfix address rewriting can help, basically i think i want linux to receive the email and then change the smtp address so instead of the mail extension being e.g. @test.local it will go to @lgfl.org.uk and then the user will receive the email through the @lgfl.org.uk. 
 
I am really new to linux and have read online material for a several hours and not really understanding it. I have found a few posts on here already that have been helpful in away but i am still none the wiser in how to actually achieve my goal.
 
If anybody can help or point in the right direction it will be greatly appreciated.
 
Thank you in advance

---


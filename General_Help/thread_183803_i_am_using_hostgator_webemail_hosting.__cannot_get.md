---
title: "i am using hostgator web/email hosting.  cannot get evolution to smtp even with auth."
date: 2006-05-28
forum: General Help
---

### Post by TOPPEL on 2006-05-28
I am using hostgator.com's web and email hosting services.  one of my add-on domains receive but not send on ubuntu.  the status bar doesn't even start with evolution.  the pop goes from left to right and completes its function.  i have tried reinstalling evolution however i am still unable to send mail.  i dont believe AT&T blocks port 25 regardless, i have it open on my router.  i have also tried thunderbird for good measure.  my host told me a connection timed out error meant that it was something on the configuration side not their servers was wrong but i've configured email clients for pop and smtp a million times and i'm stumped.  

would love to resolve this problem.  

thank you

---

### Post by amanda on 2006-05-30
I am just getting my Evolution bearings, but I found that I had to set my SMTP server to "mail.example.com:465"  in order to send mail. My host (dreamhost) doesn't support authenticated SMTP, but does accept connections over port 465. It took me a while to work that out, so maybe it will help you?

---

### Post by TOPPEL on 2006-05-31
thank you i will keep that email in reference in the event i have problems again.  it seems they may have adjusted the server a little bit because it was working fine but i had problems today due to a last minute configuration error.  all is working great now.  but thank you --

---

### Post by TOPPEL on 2006-06-09
[QUOTE=TOPPEL]thank you i will keep that email in reference in the event i have problems again.  it seems they may have adjusted the server a little bit because it was working fine but i had problems today due to a last minute configuration error.  all is working great now.  but thank you --[/QUOTE]

that is seems odd.  if your smtp doesn't have authentication anyone that knows dreamhost and your email address could send an email ?  maybe they just make you specify a port.  anyway in the long run it the error was on my side.

---


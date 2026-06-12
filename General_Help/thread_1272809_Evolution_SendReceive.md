---
title: "Evolution Send\\Receive"
date: 2009-09-22
forum: General Help
---

### Post by nh5y on 2009-09-22
Today I realized I hadn't had any new emails since Friday, so I logged into gmail to double check and found that it just wasn't downloading in evolution for some reason.  I was still able to send email, though.

I searched for an answer and tried a bunch of things, and nothing worked.  In fact, I made it worse because now I can't send email either.

I'm going to assume that whatever the original problem was doesn't matter, so right now I'm only going to discuss what is currently happening:

- I've checked\\recreated my email account preferences a million times and i think that the settings are fine
- it's linked up to one email account: my gmail (POP).
- the test email i tried to send is still in the outbox.
- when i click send\\receive, i get this message:

Error while performing operation.
MAIL FROM command failed: Authentication Required. Learn more at                              
[http://mail.google.com/support/bin/answer.py?answer=14257](http://mail.google.com/support/bin/answer.py?answer=14257) 9sm599083agc.16

- the link in the error message didn't work for me though
-  I don't think it's a problem with my gmail settings b/c 1) my email was working fine for a long time before this problem occurred, and 2) I checked it out and everything looks right to me.

any help would be awesome.  I will be around for the next hour or so (6-630 pm EST) if you need further information and I will be back online a couple hours after that.

thanks!

natasha

---

### Post by kerry_s on 2009-09-22
> Error while performing operation.
MAIL FROM command failed: Authentication Required. Learn more at
[http://mail.google.com/support/bin/a...y?answer=14257](http://mail.google.com/support/bin/a...y?answer=14257) 9sm599083agc.16


this leads me to believe your not setting it up right, your suppose to use "ssl" for both out & in. make sure your on the right ports to.

```
Incoming Mail (POP3) Server - requires SSL:  	pop.gmail.com
Use SSL: Yes
Port: 995
Outgoing Mail (SMTP) Server - requires TLS: 	smtp.gmail.com (use authentication)
Use Authentication: Yes
Use STARTTLS: Yes (some clients call this SSL)
Port: 465 or 587 
```

---

### Post by nh5y on 2009-09-22
thanks for the reply.  my account is already set up the way you specified.  any other suggestions??

---

### Post by dcstar on 2009-09-23
> **nh5y said:**
> Today I realized I hadn't had any new emails since Friday, so I logged into gmail to double check and found that it just wasn't downloading in evolution for some reason.  I was still able to send email, though.

I searched for an answer and tried a bunch of things, and nothing worked.  In fact, I made it worse because now I can't send email either.

I'm going to assume that whatever the original problem was doesn't matter, so right now I'm only going to discuss what is currently happening:

- I've checked\\recreated my email account preferences a million times and i think that the settings are fine
- it's linked up to one email account: my gmail (POP).
- the test email i tried to send is still in the outbox.
- when i click send\\receive, i get this message:

Error while performing operation.
MAIL FROM command failed: Authentication Required. Learn more at                              
[http://mail.google.com/support/bin/answer.py?answer=14257](http://mail.google.com/support/bin/answer.py?answer=14257) 9sm599083agc.16

- the link in the error message didn't work for me though
.........

This link works fine, and I suggest you put it in a browser and read its contents.

---

### Post by nh5y on 2009-09-23
thanks, david.

this morning when i tried sending a test email, it worked-- so i don't know what changed with that.  but receiving still didn't work.

the link in your quoted reply did work.  but, after following the steps on the link, nothing changed.

so receiving emails is still a problem for me and i don't know how to fix it.  any other suggestions??

thank you for all your help,

natasha

---

### Post by nh5y on 2009-09-23
actually, now i'm confused.  i just got 1 email through evolution: from WWF passport (an organization i subscribe to)

but my gmail is still full of brand new emails that HAVEN'T come through evolution.

any help with this would REALLY be appreciated

thank you,

natasha

---

### Post by bradhaack on 2009-10-14
Check your junk folder.  They can go in there & there is no counter showing new mail in the junk folder.

---


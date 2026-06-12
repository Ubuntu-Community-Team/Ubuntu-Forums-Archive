---
title: "Empathy and Google Talk with non-gmail Google account"
date: 2011-06-30
forum: General Help
---

### Post by kcstrom on 2011-06-30
I can't seem to get Empathy to work with my Google account that doesn't end in @gmail.com (it ends with @[mydomainname].com).  It works just fine with a Google account I have that is a @gmail.com username.  Is this is known issue?

FYI: Pidgin appears to do the same thing.  I can launch the Google talk applet from [http://www.google.com/talk/start.html](http://www.google.com/talk/start.html) with my non @gmail Google account and it works just fine.

---

### Post by pqwoerituytrueiwoq on 2011-06-30
try [email]kcstrom@email.school.edu@gmail.com[/email]

---

### Post by kcstrom on 2011-06-30
> **pqwoerituytrueiwoq said:**
> try [email]kcstrom@email.school.edu@gmail.com[/email]

Thanks for the suggestion.  Unfortunately, it still doesn't work. :(

---

### Post by Seq on 2011-06-30
You have to put DNS entries to point jabber services for yourdomain.com to google's jabber/xmpp servers.

[http://www.google.com/support/a/bin/answer.py?answer=34143](http://www.google.com/support/a/bin/answer.py?answer=34143)

---

### Post by kcstrom on 2011-06-30
> **Seq said:**
> You have to put DNS entries to point jabber services for yourdomain.com to google's jabber/xmpp servers.

[http://www.google.com/support/a/bin/answer.py?answer=34143](http://www.google.com/support/a/bin/answer.py?answer=34143)

Thanks for the information.  Unfortunately, my web hosting company doesn't allow me to edit the SRV settings.  It seems strange that I would have to do this as my non @gmail.com Google account is just an account name for Google's system - I don't see why any chat client would need to actually do anything with my domain.

Ross S.

---

### Post by Seq on 2011-07-01
> **kcstrom said:**
> Thanks for the information.  Unfortunately, my web hosting company doesn't allow me to edit the SRV settings.  It seems strange that I would have to do this as my non @gmail.com Google account is just an account name for Google's system - I don't see why any chat client would need to actually do anything with my domain.

Ross S.

If somebody were to add you, [email]kcstrom@yourdomain.com[/email], how would their chat client know that it actually has to talk to google instead of an xmpp server at yourdomain.com? That is what the SRV values are for.

---

### Post by kcstrom on 2011-07-01
> **Seq said:**
> If somebody were to add you, [EMAIL="kcstrom@yourdomain.com"]kcstrom@yourdomain.com[/EMAIL], how would their chat client know that it actually has to talk to google instead of an xmpp server at yourdomain.com? That is what the SRV values are for.

That makes sense if it tires to send the message directly to the domain.  I was thinking messages went to Google who routed them based on the Google account being used.  Sounds like that is not how the underlying protocol works.

Ross S.

---

### Post by Seq on 2011-07-02
> **kcstrom said:**
> That makes sense if it tires to send the message directly to the domain.  I was thinking messages went to Google who routed them based on the Google account being used.  Sounds like that is not how the underlying protocol works.

Ross S.

For a closed network, such as MSN, that is true. [email]jack@msn.com[/email] can talk to [email]jill@hill.com[/email] since everything goes through MSN's servers. However, Google Talk is actually just one server in the larger federated XMPP network, and most of that network is not controlled by Google.

I could install jabberd on myserver.com, create a bunch of accounts, and start messaging google talk users. When a Google user messages me, sends the message to myserver,com. If I decide that even though my account names are "myserver.com", but my chat server is actually at "talk.myserver.com", I need to create a DNS record to let everybody know. Think of it like an MX record does for mail.

As for google talk working through their website, when a google user tries to send you a message, it is intelligent enough to say "I'm hosting that domain and chat is enabled, and he's signed on now. Therefore, route it internally". So you're right that messages ideally go via google. But the clients probably can't figure out how to work properly under 'standard' conditions since the required DNS records are not there, and you're not using an end-to-end google-coded solution.

---

### Post by kcstrom on 2011-07-02
Hi Seq, thanks for that explanation, that makes sense.

---


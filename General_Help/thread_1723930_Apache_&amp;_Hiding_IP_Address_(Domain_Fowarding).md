---
title: "Apache &amp; Hiding IP Address (Domain Fowarding)"
date: 2011-04-07
forum: General Help
---

### Post by scottyf11 on 2011-04-07
I setup apache to host a website, and the domain redirect from Misk works fine.  My only problem is that when it redirects, my IP address shows in the address bar instead of my domainname.com

The website is [www.woolsisters.com](www.woolsisters.com) if it matters.

Thanks!

---

### Post by spikoley on 2011-04-08
The problem is that you are using a URL Redirect.  It is working exactly like it should.  You don't want to forward it, you want to point it.

To set this up correctly you need to set up an A Record in the Host Records for the domain.  Go into the zone records for the domain.  They may call it "host records" or "advanced DNS".

You will need to modify three records.  It should look like this when you are done.
```

www    A Address    68.114.80.28
@      A Address    68.114.80.28
*      A Address    68.114.80.28

```
The www is when you type www in front of the domain.  The @ is the domain by itself and the * is the catch all.  They might use different terms, but it should look something like that.

---

### Post by scottyf11 on 2011-04-08
Hmm the only thing I can update is the nameserver?

---

### Post by spikoley on 2011-04-08
> **scottyf11 said:**
> Hmm the only thing I can update is the nameserver?

Contact their support.  You should have a way to update the records.

---


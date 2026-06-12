---
title: "/usr/bin/mail"
date: 2011-03-30
forum: General Help
---

### Post by Drenriza on 2011-03-30
I have a problem of sort.

I try to send an e-mail to myself (two different machines) from a linux server. But for some reason i don't receive it. My questions are.
#1 Does anyone know what port and protocol the /usr/bin/mail program use?
#2 Does anyone know of a quick way to check if this port is open?

Thanks on advance.
Kind regards.

---

### Post by blind2314 on 2011-03-30
If you want to just send mail, no port needs to be specially opened. However, to receive mail with /usr/bin/mail, you need a running SMTP server (which requires port 25).
 
There are plenty of guides out there on the interwebs, or I can help if you'd like.

---

### Post by d3v1150m471c on 2011-03-30
```

sudo apt-get install bsd-mailx

```

^ that's what i use, and it does work behind a router without portforwarding, oddly enough.

---


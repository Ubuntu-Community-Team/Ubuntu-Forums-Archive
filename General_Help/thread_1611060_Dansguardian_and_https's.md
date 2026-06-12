---
title: "Dansguardian and https's"
date: 2010-11-01
forum: General Help
---

### Post by Periswell on 2010-11-01
Hello

I have installed Dansguardian on my little brothers laptop (using Tinyproxy and Firehol too) and I have it mostly configured the way I like it. The only problem now is that I can't seem to block secure ([https://www](https://www)...) websites, and he knows a few proxies that use secure domains. I was wondering if anyone has been able to make Dansguardian block these websites or is it just not doable? Thank you in advance.

-Joshua

---

### Post by Jordy_224 on 2011-07-26
Hello, i'm not sure if you are still interested in this thread but I came across the same problem. You can edit the url block pages file in the dansguardian folder to include https sites:

```

/etc/dansguardian/lists/bannedurllists.txt
```

 I would say this is the first tier defense against https proxies. There are several other layers of defense that I found out over time works. I posted a guide on another thread. 

Do [SIZE="2"]**whatever**[/SIZE] it takes to protect your younger brother!

---


---
title: "Problems with wget"
date: 2009-07-04
forum: General Help
---

### Post by Uncle_Grombor on 2009-07-04
I attempted to add Cathbard's repo to my list when I discovered that wget will not work. I tried it with a few sites and I get this same error every time. Error parsing proxy URL [http://localhost:4001](http://localhost:4001) : Bad port number. Anyone have any ideas? As far as I know, I am not using a proxy.  Thanks

---

### Post by Boondoklife on 2009-07-04
Can you post the command as you are running it?

---

### Post by andrew.46 on 2009-07-05
Hi Uncle_Grombor,

> **Uncle_Grombor said:**
> I attempted to add Cathbard's repo to my list when I discovered that wget will not work. I tried it with a few sites and I get this same error every time. Error parsing proxy URL [http://localhost:4001](http://localhost:4001) : Bad port number. Anyone have any ideas? As far as I know, I am not using a proxy.  Thanks

It is not a solution as such but a work-around might be:

```
wget --no-proxy *etc etc*
```

From the man page:

```

--no-proxy
Don't use proxies, even if the appropriate *_proxy environment
variable is defined.

```

Might be worth a try?

Andrew

---

### Post by Uncle_Grombor on 2009-07-05
I was able to get wget to run, but I have one last question.  For some reason Apt and Wget (apt either from term or synaptic) bounces between 500 bps to 40 Kbps. Firefox runs downloads as it should at around 180 Kbps. Anyone know why there could be such a large difference, and why the one is choppy and the other gives me the appropriate speeds for my service? wget and apt run like this no matter the site or the mirror. It also acts like this for updates too. I felt it may have been something to do with my IP so I tried this website, but still no correction to problem.  [http://www.cyberciti.biz/faq/howto-linux-renew-dhcp-client-ip-address/](http://www.cyberciti.biz/faq/howto-linux-renew-dhcp-client-ip-address/)

Thanks.

---


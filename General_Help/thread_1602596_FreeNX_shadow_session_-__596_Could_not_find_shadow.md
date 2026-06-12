---
title: "FreeNX shadow session -  596 Could not find shadowed session"
date: 2010-10-21
forum: General Help
---

### Post by Lucky75 on 2010-10-21
Hi!

I'm trying to connect to my display :0 using a shadow session on freenx. Two different options pop up, both apparently on display :0, but I get the following message:

```

NX> 596 Could not find shadowed session XXXXXXXXXXXXXXXXXXXXXX. Session failed.
NX> 596 Sharing: 
NX> 105 NX> 280 Exiting on signal: 15

```Does anyone know how to get it to work? I'm logging in with the same username as the connected session (so I shouldn't have to touch /etc/nxserver/nxshadowacl).

Also, how would I get it to work with multiple monitors? It seems to collapse itself onto one monitor right now when I log in with a new session.

I also can't seem to restart freenx-server. Is it restarting anyway? Any solutions for this one?
```

stop: Unknown instance:
start: Job failed to start

```Any suggestions? I've tried looking on google but no one seems to have an answer, so I was hoping someone here would be so kind.

Thanks!


------------------------------------------------

Edit: It would seem that installing it from nomachines manually instead of through the repository works better. I can now connect to my session properly. 

However, still having issues with multiple monitors. Now it just compresses both monitors to fit on one monitor. Is there any way of having it be full size and just let me scroll to see the rest? Or have it attach to two sessions, one per monitor? I mean, I could do that if I was using multiple X sessions instead of twinview, but that's kind of useless.

Thanks!

---


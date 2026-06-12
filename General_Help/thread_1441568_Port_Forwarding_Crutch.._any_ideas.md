---
title: "Port Forwarding Crutch.. any ideas?"
date: 2010-03-28
forum: General Help
---

### Post by ToshiBoy on 2010-03-28
I'm not that great with mailservers, and just been thrown a curveball with a MS Exchange environment for which there is apparently no solution... yeah, right. But is there a workaround?

The problem is that the site mail (SMTP) needs to be sent via port 26 instead of the commonly used 25. Port 25 is mapped to a mailfilter, which apparently causes havoc with some of the mail, and the techs that have been on site trying to coax the Exchange server to co-operate have said that the only way would be to get rid of the filter.

The problem is that there are number of apps that are unable to have the outgoing port changed and so keep sending mail out on port 25.

I look after the Unix/Linux side of things at work, and I was wondering if there was an easy way to set up a Ubuntu box to receive mail on port 25 and just forward it to the MS box on port 26? So, in other words (and I hope this makes sense): monitor port 25, and forward whatever comes in on port 25 to the server on port 26. Simple portforwarding, or is it? What steps do I need to take?

---

### Post by nemilar on 2010-03-28
I'm not sure how to do it (yet) but I know what you want to do can be accomplished with iptables using port redirection.

Sorry I can't be more helpful at the moment, but maybe that can help you with somewhere to start googling.  "iptables port redirection".

---

### Post by ToshiBoy on 2010-03-28
Spot on Nemilar. Thank you for pointing me in the right direction. Exactly what I was after.

Regards

Toshi

---


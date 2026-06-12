---
title: "Cannot get my Realtek Integrated Onboard Network Connection - RTL8100C - to work?"
date: 2010-01-05
forum: General Help
---

### Post by Bluesplayer on 2010-01-05
Hi

I have just bought a new base unit with Integrated Onboard Network Connection - RTL8100C - which I can't for the life of me get to work with the ubuntu server.  I have tried a number of things I found on this forum but to no avail.  How can I get the damn thing to switch on or be recognized?

Regards

---

### Post by dcstar on 2010-01-06
> **Bluesplayer said:**
> Hi

I have just bought a new base unit with Integrated Onboard Network Connection - RTL8100C - which I can't for the life of me get to work with the ubuntu server.  I have tried a number of things I found on this forum but to no avail.  How can I get the damn thing to switch on or be recognized?

Regards

You need to examine the syslog file for the relevant entries.

---

### Post by Bluesplayer on 2010-01-06
> You need to examine the syslog file for the relevant entries.

Can you ellaborate on this a bit more please?  If I find these entries what then?

---

### Post by Bluesplayer on 2010-01-09
Hi

I followed a number of topic suggestions and I have been able to activate the disabled network using this command string:

```
sudo ifconfig eth1 up
```Even though the network is now enabled it still isn't working.  What do I need to do now to get my server back online?

Regards

As a side note.  Can my server be run with Ubuntu Desktop?  Probably the lan will work then.

---


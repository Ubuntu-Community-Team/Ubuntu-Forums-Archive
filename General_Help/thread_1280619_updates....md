---
title: "updates..."
date: 2009-10-02
forum: General Help
---

### Post by phalgun on 2009-10-02
hello..
Im new to this forum so im not sure if this is the right place to post this..

I recently installed ubunto v9.04 on my desktop(we have unix as a subject in college)and realized that updates are necessary for a lot of programs(media etc).The problem is i dont have a net connection to my desktop.So is there a way where i can download the necessary updates onto my laptop(Windows Vista and has a net connection) and then install those updates on my desktop?

Cheers!:)

---

### Post by Giblet5 on 2009-10-02
You have a network connection for Windows but not for linux?

And you're studying linux in school?

You can't share the connection?


Plan B would be to download the daily build .iso image and reinstall. That'd be a lot easier than trying to manually update via a manual Windows proxy.

See [RFC1149]("http://www.faqs.org/rfcs/rfc1149.html") for a possible workaround.

---

### Post by 321sebo123 on 2009-10-02
> **Giblet5 said:**
> 
See [RFC1149]("http://www.faqs.org/rfcs/rfc1149.html") for a possible workaround.

IPoAC - yes, it may be a fix for your connection problem - but packet lost ratio over IPoAC is ca 55% so it may take longer time needed for retransmissions of lost packets.

/S

---

### Post by Giblet5 on 2009-10-02
> **321sebo123 said:**
> IPoAC - yes, it may be a fix for your connection problem - but packet lost ratio over IPoAC is ca 55% so it may take longer time needed for retransmissions of lost packets.

/S


That, plus one doesn't need to stuff stale bread into an ethernet switch... I never said it was a *perfect* workaround.

---


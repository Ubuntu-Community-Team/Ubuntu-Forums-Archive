---
title: "https is slow"
date: 2010-09-25
forum: General Help
---

### Post by oneadvent on 2010-09-25
Any websites that are https (ssl) load very slowly or are intermittent. For example, gmail is very very intermittent if it comes up at all. And takes a long time to do anything. I have a 64 bit Ubuntu 10.04 on a Gateway laptop. I am using a PCMCIA wireless card that used to work fine in the past.

I have Chrome, Chromium, and FF, and all of them have the same problem. I'm not sure what is up with it. I have another laptop, 32 bit Ubuntu 10.04, a Sony with no issues at all. I am using wep for security, and it authenticates fine. Ping tests reveal no issue. I let them go on for 400ish pings and no loss and average trip time of 32 ms, so I am not suspecting my ISP.

any ideas would be appreciated.

---

### Post by oneadvent on 2010-09-27
selfless BUMP

---

### Post by oneadvent on 2010-10-02
bump again, i really need to get some advice here guys.

---

### Post by oneadvent on 2010-10-16
Although no replies, I have diligently been working on this problem, and have discovered that wired ethernet works fine. I am going to go ahead and get another pcimcia card and see what happens with that.

Will post when i do.

---

### Post by oneadvent on 2010-10-24
wow I am having some trouble. Any one out there have some suggestions, the new card didn't help.

---

### Post by dajare on 2011-11-07
Sorry to say, this is just a "me too" post. I recently upgraded to Lubuntu 11.10 after spending a couple years with a trouble-free but now un-updatable Jaunty 9.04.

What is described here is exactly my scenario. "Ordinary" sites load beautifully. Gmail loads ... sometimes, rarely quickly, and other times not at all. At the same time, sites like bbc.co.uk, a random example, load up right away. I'm normally in Chromium, but the same issue affects Firefox and Opera as well.

I just upgraded over this past weekend. I had noticed this behaviour when running the live CD, but hoped it would go away with a full install. I never had them with 9.04.

Not sure how to diagnose this! Hoping, like oneadvent, that someone can shed some light (and suggest a fix!) for this.

---

### Post by linuxwin2 on 2011-11-08
What's the version of your browser.
Check SSL settings (TLS1.0 SSL2.0 SSL3.0..) in your browser

---

### Post by dajare on 2011-11-08
> **linuxwin2 said:**
> What's the version of your browser.
Check SSL settings (TLS1.0 SSL2.0 SSL3.0..) in your browser

Browser = 14.0.835.202 (Developer Build 103287 Linux) Ubuntu 11.10

SSL settings =  Check for server certificate revocation; Use SSL 3.0; Use TLS 1.0 = all "on".

I've done quite a bit of googling on this one, and it seems to have come-and-gone over the various versions. No one (in the many things I've found) seems to have worked out quite what's going on here.

Wee shame! :confused:

---


---
title: "Awstats reports US traffic is first on all webhosts for a belgian server!"
date: 2009-07-24
forum: General Help
---

### Post by VinzC on 2009-07-24
Hi.

I'm running Ubuntu 8.04 on a server at OVH. I've installed **awstats-6.7** (the latest available on that branch). It essentially holds web sites for Belgian/European audiences. On each of the sites I've installed, *awstats* reports US traffic is by far the most important, e.g. between 5 and 10 times the bandwidth for Belgium.

I haven't been able to distinguish what is responsible in the stats for such traffic. Details by hosts, for instance, don't show any US endpoints. Can anyone help?

Thanks in advance.

---

### Post by VinzC on 2009-07-24
I've checked the IP addresses from the United States and it turns out most of them are IP addresses from web crawlers (Google, Yahoo, MSN, aso). I just wonder why awstats takes them into account to compute the bandwidth...

---

### Post by LepeKaname on 2009-07-24
I believe you can setup Awstats to ignore bots hits. 
This link may be useful: [http://www.petersblog.org/tag/awstats](http://www.petersblog.org/tag/awstats)

Some stats systems (I'm not sure about AWStats) assume that ".com" domains (from redirected urls) are from US sites, ignoring the server location (when IP to location is not available).

---

### Post by VinzC on 2009-07-25
> **LepeKaname said:**
> I believe you can setup Awstats to ignore bots hits. 
This link may be useful: [http://www.petersblog.org/tag/awstats](http://www.petersblog.org/tag/awstats)

Some stats systems (I'm not sure about AWStats) assume that ".com" domains (from redirected urls) are from US sites, ignoring the server location (when IP to location is not available).

Thanks a lot for the link, I was looking for something to analyze my logs.

BTW I think I remember awstats by default ignores webbots. Unless all of them changed the way they're working between 6.7 and the current 6.9... (Everything is possible in this world.)

As far as the redirection from .com is concerned, I also thought about such a «feature». However the bandwidth usage should be limited and in no circumstance more important than that drawn from the main web site. Currently the US traffic eats all of the bandwidth... Annoying.

I'll try a fine grained analysis, let's see.

---


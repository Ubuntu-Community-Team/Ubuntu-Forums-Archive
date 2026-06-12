---
title: "High CPU 92-100 %"
date: 2012-02-20
forum: General Help
---

### Post by mk5500 on 2012-02-20
I put lubuntu on a P3 733mhz PC, 512mb and just use this PC to listen to Google music.

Nothing else -- no apps are installed at all.

So when I'm listening, through the chromium browser it's stuttering lately -- went to task manager and see CPU usage is 92 to 100, YET, when I look at individual processes there are only 2 showing, chromium at about 27% and lxtask? (can't remember) at 17% -- NOTHING else.

What the heck is going on you think?

I may have to reinstall lubuntu?

---

### Post by Gremlinzzz on 2012-02-20
I would try another system.-if you don't mind installing :popcorn:

---

### Post by mk5500 on 2012-02-20
P3 too lean for Lubuntu?

That's why I went with it -- all the claims of performance on older systems and actually at first I was impressed.

May try to reinstall first. What puzzles me is why I don't see another task that would add up to the high CPU use -- just those 2 things, chromium and lxtask (or whatever it is)

---

### Post by Gremlinzzz on 2012-02-20
Give this a try live cd 
The desktop CD allows you to try Ubuntu without changing your computer at all, and at your option to install it permanently later. This type of CD is what most people will want to use. You will need at least 256MiB of RAM to install from this CD.

[http://distrowatch.com/?newsid=07112](http://distrowatch.com/?newsid=07112)

:popcorn:

---

### Post by sanderj on 2012-02-20
> **mk5500 said:**
> I put lubuntu on a P3 733mhz PC, 512mb and just use this PC to listen to Google music.

Nothing else -- no apps are installed at all.

So when I'm listening, through the chromium browser it's stuttering lately -- went to task manager and see CPU usage is 92 to 100, YET, when I look at individual processes there are only 2 showing, chromium at about 27% and lxtask? (can't remember) at 17% -- NOTHING else.

What the heck is going on you think?

I may have to reinstall lubuntu?

Before doing that, first stop Chrome/Chromium, and start using Midori. AFAIK Chrome is memory hungry.

I have a 256MB Xubuntu, and as soon as Firefox is running, it is slooooowwwwww ...

Tip: type 'uptime' and look at the last three numbers: Below 1.00 is OK, above 5.00 is very bad ...

---

### Post by mk5500 on 2012-02-20
sounds good thanks.

---

### Post by sudodus on 2012-02-20
... and/or install ***htop*** with
```
sudo apt-get install htop
``` It will show you very clearly which processes are running and how much cpu and memory they use.

I think Lubuntu + Chromium would work with 512 MB RAM. If not, try some lean browser, as suggested by *sanderj*! But I think that there is some other process, that is causing problems. Maybe it was updating the software in the back-ground.

---


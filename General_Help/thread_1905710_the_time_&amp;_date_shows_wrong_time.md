---
title: "the time &amp; date shows wrong time"
date: 2012-01-07
forum: General Help
---

### Post by zouyong on 2012-01-07
I've changed to my current location but the time is still wrong.
At first I thought it was because of my time zone, but even the showing minutes is wrong. 
I use ubuntu 11.10. 
I've install ntp but still it doesn't work.
Is there anyone can help me?
Thanks

---

### Post by dcstar on 2012-01-08
> **zouyong said:**
> I've changed to my current location but the time is still wrong.
At first I thought it was because of my time zone, but even the showing minutes is wrong. 
I use ubuntu 11.10. 
I've install ntp but still it doesn't work.
Is there anyone can help me?
Thanks

**Exactly** how wrong? And what Timezone/Location are you in?

I have seen another forum post recently with similar issues.

---

### Post by zouyong on 2012-01-08
Never mind, it is ok now. 

No idea of whether by default ntp is installed or not, I installed this ntp again yesterday but still when I choose different locations on the time&date maps, the showing time is wrong(not just the hour, but even the minute is wrong). 

I'm in denver timezone. Before when I installed ubuntu 11.10, I choose this denver timezone, the time is wrong so I just choose a timezone named UTC which is similar as my real time. 

Yesterday(I just could't stand this wrong timezone anymore so I tried to fix this) after I installed this ntp and I added denver as one of my timezone(the other is this UTC), and choose automatically from the internet. I thought it could immediately synchronize with internet time, but still it doesn't work(I rebooted my machine several times). Then I just didn't remove this denver timezone but still use UTC.

But today after I opened my machine, I found denver's clock is correct.

No matter what, thanks.

---

### Post by oldos2er on 2012-01-08
> **zouyong said:**
> I'm in denver timezone. 

So am I. About once a month or so I run ```
sudo ntpdate time.nist.gov
```

---


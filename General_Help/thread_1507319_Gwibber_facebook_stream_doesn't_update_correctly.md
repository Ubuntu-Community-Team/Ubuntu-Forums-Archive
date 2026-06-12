---
title: "Gwibber facebook stream doesn't update correctly"
date: 2010-06-11
forum: General Help
---

### Post by tendonstrength on 2010-06-11
I'm having a problem with my Facebook stream in Gwibber. Sometimes it runs fine, but sometimes it doesn't refresh the stream for hours at a time. Even if I manually refresh the stream, it doesn't load the most current updates.

I also tried setting the stream to update every minute instead of every 5 minutes and that doesn't seem to help either. 

Anyone else having this issue?

---

### Post by noushii on 2010-06-12
Yup, not only with facebook but with twitter too.

---

### Post by tendonstrength on 2010-06-14
Now that you mention it, I am also having the problem with Twitter as well.

---

### Post by wbm on 2010-06-14
To me it looks like Gwibber came all together broken in 10.04. It worked much better with the version that came in 9.1.
Maybe they should just remove it from the repositories until they have a working version again.

---

### Post by luiz.gregorio on 2010-06-14
This is not a v10.04 issue, in fact I am still using v9.10 and for the last 2 weeks FB stream is giving me some bad headaches.

It is not updating correctly, sometimes it does and sometimes it doesn't, couldn't determine a pattern yet. Manual updates are also useless

Have tried to change timeout values on facelib.py but nothing seems to work, unfortunately

---

### Post by kenzter on 2010-06-14
Same thing here. Wonder why they cant fix this ...

---

### Post by tom.swartz07 on 2010-06-14
I have a keen thought that it might be the API thats broken from time to time. It doesnt affect just Gwibber, but everything, my iPhone cant get it for about an hour now.

Sometimes Twitter and Facebook break the API for an hour or two while the do upgrades.

Thats usually the cause of the big white failwhale on Twitter most of the time.

---

### Post by wbm on 2010-06-15
> **luiz.gregorio said:**
> This is not a v10.04 issue, in fact I am still using v9.10 and for the last 2 weeks FB stream is giving me some bad headaches.

It is not updating correctly, sometimes it does and sometimes it doesn't, couldn't determine a pattern yet. Manual updates are also useless

Have tried to change timeout values on facelib.py but nothing seems to work, unfortunately

Hello,
I know that it is not a 10.04 issue. What I meant is, that the Gwibber version that was available during the 9.1 days a few weeks/month back worked a lot better. It also had more functionality.

---

### Post by tendonstrength on 2010-06-15
Did some checking and it looks like there is a bug for this in the Gwibber launchpad DB:

[https://bugs.launchpad.net/gwibber/+bug/533017](https://bugs.launchpad.net/gwibber/+bug/533017)

I haven't tried any of the workarounds suggested yet although the one suggested in comment #25 looks promising. I'll try it when I have some time.

---

### Post by tendonstrength on 2010-06-15
I tried it, but it doesn't seem to work. My default locale already looked ok. I reset it again just to be sure, but it didn't help, even after a reboot.

---

### Post by luiz.gregorio on 2010-06-15
Have tried almost all ideas, changing language, setting diff timeout values on facelib.py, some say to try to use OpenDNS but I am not sure about it. You may give it a try.

From my side, I hope to have a new version soon and these problems to be solved on it

---

### Post by tendonstrength on 2010-06-16
In the grand scheme of things this is not a big deal, but it would be nice if they could fix it, especially since "social from the start" is one of the marketing slogans for Lucid.

---

### Post by jivimberg on 2010-06-16
Same problem here!

Already tried some of the proposed workarounds of the bug report with no result.

Hope somebody finds a solution soon!

---

### Post by tendonstrength on 2010-07-16
It looks like there was a fix for this released today. I guess Facebook was throttling the API, so the Gwibber team made the API calls more efficient by downloading only new data when refreshing the stream. The fix seems to be working for me so far. 

Kudos to the Gwibber team wherever they may be.

---

### Post by jivimberg on 2010-07-18
It's working for me too! Glad they fix this...
 
Anyway, still not working for facebook images :S and no popup notification for facebook either

---

### Post by wbm on 2010-07-19
It has improved for me too. The updates seem to work again, but the previous (working) version was still better as it showed images and threads much better.

---

### Post by lasnaghi on 2011-02-08
Using Ubuntu 10.10 on 64-bit platform and Gwibber keeps dying on me. No updating, no nothing. Tried several suggestions listed here and in other groups, to no avail. I did a complete reinstall to see if that would help, but Twitter/identi.ca still stop updating.

---

### Post by Draky on 2011-02-13
Got a similar problem : I wrote sometjhing to FB.
I told Gwibber to delete but it's still here !

I need to go to the web page of FB to delete it and then it is still in Gwibber but no more ein FB.
Same for Twitter.

---


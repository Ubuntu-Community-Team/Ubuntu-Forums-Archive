---
title: "Podcast Filenames in Rhythmbox"
date: 2010-08-03
forum: General Help
---

### Post by Mr_Lazy on 2010-08-03
Hi,

Rhythmbox has started renaming the files it is downloading, started after a new install of Lucid (I think).

Example:
[http://downloads.bbc.co.uk/podcasts/fivelive/kermode/rss.xml](http://downloads.bbc.co.uk/podcasts/fivelive/kermode/rss.xml)

The filename should be:
**kermode_20100730-1909a.mp3**

but after Rhythmbox has downloaded it, it is:
[B]http---downloads.bbc.co.uk-podcasts-fivelive-kermode-kermode-20100730-1909a.mp3
[/B]
Does anyone know why this is happening? I have looked around thinking this must be a really common problem, but I can't find the cause.  Also, it is not just BBC podcasts, it is ALL podcasts....

Thanks in advance,
Stephen

---

### Post by sclaughl on 2010-08-15
I noticed the same thing, and it's an annoying problem. I think it must be a regression stemming from the fix for bug #445141. [https://bugs.launchpad.net/ubuntu/lucid/+source/rhythmbox/+bug/445141](https://bugs.launchpad.net/ubuntu/lucid/+source/rhythmbox/+bug/445141)

Unsure if I should open a ticket for this, or what?


--Stuart

---

### Post by BrianH_1 on 2011-10-29
Has there been any resolution to the first post in this thread?

I have had the same problem since Lucid but just got frustrated enough to look for a fix - and do not see a resolution in link posted by Stuart.

Here are some examples:
Podcast filename given by Rhythmbox:

http---mpegmedia.abc.net.au-rn-podcast-2011-07-bia-20110710.mp3

Should be: bia-20110710.mp3

Podcast filename given by Rhythmbox:

http---podcast.cbc.ca-mp3-podcasts-aop-20110514-37754.mp3

Should be:aop-20110514-37754.mp3

Any help would be appreciated.

BHH

---

### Post by sclaughl on 2011-11-23
FWIW rhythmbox eventually went 'back to normal' for me. I'm sorry to say that I can't offer any additional information -- it's been too long, and I'm not sure I ever knew! I'm assuming it was probably an upgrade somewhere along the line.

At any rate, I'm no longer observing this problem.

---


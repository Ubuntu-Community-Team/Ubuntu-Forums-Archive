---
title: "Download managers and resuming downloads"
date: 2011-04-09
forum: General Help
---

### Post by malleeblue on 2011-04-09
I have tried [so many download managers]("http://ubuntuforums.org/showthread.php?t=1023698") it ain't funny, but there's one thing they all don't seem to know how to do well, and that's resume problematic downloads.

I have used both fast and slow Internet connections on 3 continents (currently I'm on a slow and intermittent one as I live in Burma) so speed doesn't seem to be what causes the problem. And I download from many, many different sites, so it's not site specific either.

The problem is as follows. I'm downloading a file **from a server that supports resuming downloads** but something goes wrong with the download and the download manager reports an error, like "size mismatch", or "timeout error".

What I really, really want to know, is why can't these managers resume downloads that experience these errors? Why can't they set markers during the download process (say every 5MB) so that if a problem like a size mismatch, a connection dropout, or a timeout occurs, then it can backtrack only slightly and then resume? I download a couple of shows from revision3 each week and more often than I care to remember they've failed at around 70% of a 300MB+ download and merrily just start downloading all over again. Another frustrating thing is they ditch the file that didn't finish, so I can't even watch the part of the show I had.

I live with it, though it's very frustrating, but I wonder why these download managers aren't more intelligent.

Please help me understand, or better still, help me to solve the problem.

---

### Post by malleeblue on 2011-04-20
After having to re-download about another 2gb since my last post I thought I'd give this a bump hoping someone can shed some light on the topic.

---

### Post by ubun2warrior on 2011-04-20
i think u can try gwget. i have tried and worked well. it resumes downloads also.

---

### Post by malleeblue on 2011-04-20
> **ubun2warrior said:**
> i think u can try gwget. i have tried and worked well. it resumes downloads also.

Thx for your reply ubun2warrior, but my issue isn't finding a download manager that can resume, it's finding one that can resume under certain circumstances. Have another read of this topic and the one it links to and you'll get the full picture.

---

### Post by malleeblue on 2012-09-09
Just thought I'd update my own thread to say that I'm still in the same boat as when I originally posted.

I'm still after the "why", and especially still looking for a solution.

---

### Post by critin on 2012-09-09
> **malleeblue said:**
> Just thought I'd update my own thread to say that I'm still in the same boat as when I originally posted.

I'm still after the "why", and especially still looking for a solution.

  download and the download manager reports an error, like "size mismatch", or "timeout error".

the **Down Them All **extension for Firefox.  It might do what you want.
I've had these issues and chose to start a new download later.  I noticed that the first download was still in the list and had begun again from where it stopped, so canceled the second.  

Whether it stopped for the 'size mismatch' as your did, I don't know.   I believe it was something to do with dropped packages though.  All I can do is recommend to try.   It works better than any "torrent I've tried.  (for me)

---

### Post by malleeblue on 2012-09-09
> **critin said:**
> the **Down Them All **extension for Firefox.  It does what you want.

Thanks for trying critin, but in my OP I linked to [another post of mine]("http://ubuntuforums.org/showpost.php?p=6449308&postcount=1") that say, "It mustn't be browser dependent (like DownThemAll) as I like to restart my browser without affecting my download manager or having to revisit it to restart downloads."

In addition, DownThemAll doesn't do what I want. In fact, it was DTA that got me posting this thread in the first place. It was constantly giving the errors mentioned and restarting downloads **from the beginning**.

---

### Post by critin on 2012-09-09
> **malleeblue said:**
> Thanks for trying critin, but in my OP I linked to [another post of mine]("http://ubuntuforums.org/showpost.php?p=6449308&postcount=1") that say, "It mustn't be browser dependent (like DownThemAll) .


> **_NB:_** May I request that if you're going to suggest a solution that it at least meets my "what I'm after" list above, thank you.In the linked post, I admit I only read the list of DM you'd tried, I didn't read the entire post since it was very old and lengthy.   I should have, I would have seen this line and passed on it.

I did read this entire post though,  with this question, which is different from the linked.

> **Download managers and resuming downloads**
         I have tried [so many download managers]("http://ubuntuforums.org/showthread.php?t=1023698") it ain't funny, but there's one thing they all don't seem to know how to do well, and that's resume problematic downloads.Looks like there is no DM that will meet all your needs--sorry.

---

### Post by GreenWhite on 2012-09-09
Unfortunately, no download manager for linux comes close to idm or mass downloader. Its a shame, really.


     I use uget and I think this is the best downloader for linux with gui.

---


---
title: "apt-get update hang."
date: 2010-03-27
forum: General Help
---

### Post by NiGhtMarEs0nWax on 2010-03-27
for some reason i cant to and apt-get update, it seems the sources are fetched ok, bit it hangs at the very end with:

```
98% [Waiting for headers]
```

it will sit like that for ages.

any ideas?

---

### Post by derekeverett on 2010-03-28
I've been getting the same for days now.

I'm just waiting it out for now.

---

### Post by pastalavista on 2010-03-28
I've discovered my culprit was the Google repositories I added when I installed the Chrome Browser. If I uncheck the Google repository in System-->Administration-->Software Sources, the update doesn't hang, but then I don't get Chrome updates either. I just check the box for that repo once or twice a month now.

---

### Post by derekeverett on 2010-03-28
> **pastalavista said:**
> I've discovered my culprit was the Google repositories I added when I installed the Chrome Browser. If I uncheck the Google repository in System-->Administration-->Software Sources, the update doesn't hang, but then I don't get Chrome updates either. I just check the box for that repo once or twice a month now.

That's likely my problem too then. I was wondering about that.. as my problems started the day I added Chrome.

Thanks for that.

---

### Post by NiGhtMarEs0nWax on 2010-03-28
Yeh, thanks, it was the same for me, seems to have fixed it, firefox is better anyway. :P

---

### Post by _h_ on 2010-03-28
> **derekeverett said:**
> as my problems started the day I added Chrome.

Alot of people been having issues with the Google repo causing apt-get's to hang , wonder if Google is aware of the issue?

---

### Post by derekeverett on 2010-03-29
Just for the record.. this was my problem too. Everything is fine now that I removed the Google repo.

Silly Google. No wonder we're all soon to be googlin' with Yahoo!
:lolflag:

---

### Post by qbxk on 2010-04-05
Yep, a good question, and they are, 
[http://code.google.com/p/chromium/issues/detail?id=38608](http://code.google.com/p/chromium/issues/detail?id=38608)

and some recent activity on it too, which is nice.  Seems to be a unique expectation from apt-get and their server is not providing that.

---

### Post by fooey on 2010-04-07
awesome. this fixed my annoying problem too. 
[IMG]http://www.acurazine.com/forums/images/smilies/thumbsup.gif[/IMG]

---

### Post by pastalavista on 2010-04-09
Here's something we can do that's supposed to fix the problem

[http://www.webupd8.org/2010/04/fix-google-chrome-repository-making-apt.html]("http://www.webupd8.org/2010/04/fix-google-chrome-repository-making-apt.html")

---


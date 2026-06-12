---
title: "Speakers popping"
date: 2010-02-10
forum: General Help
---

### Post by at2smithjason on 2010-02-10
Every so often, my speakers will pop.  I just installed the newest release of ubuntu.  Is there something that I can download to make this stop?

---

### Post by flippo on 2010-02-11
Try running alsamixer, sometimes if some of your volume settings are too high it can cause overflow and your sound will crackle on loud noises.  Or are you talking about some other type of issue?

---

### Post by at2smithjason on 2010-02-11
It does it when the volume is all the way up, down, and muted.  It doesnt matter what the setting is.  Is there a driver that I can get?  I also looked up the program that you suggested, but I am still rather new with Linux and I would like to get some help with it.  Thanks.

---

### Post by audiomick on 2010-02-11
Hi.
I have seen a number of threads on what I think is the same issue. It seems that the power saving mechanism turns off the sound card after a while, causing a click in the speakers. Mine doesn't do it, but does click when I turn the computer off, and when something with audio content starts.

I haven't seen what I consider to be an elegant solution to this, and in my opinion the sound system needs some work because of this. One workaround that I have seen involved a script that sent a usage message to the sound driver regularly, thereby keeping it awake. I don't remember exactly how it worked.

Try searching the forum using "popping speakers" as a search criterion. I think you will find a number of threads dealing with the topic, and maybe a good solution.

---

### Post by at2smithjason on 2010-02-11
> **audiomick said:**
> Hi.
I have seen a number of threads on what I think is the same issue. It seems that the power saving mechanism turns off the sound card after a while, causing a click in the speakers. Mine doesn't do it, but does click when I turn the computer off, and when something with audio content starts.

I haven't seen what I consider to be an elegant solution to this, and in my opinion the sound system needs some work because of this. One workaround that I have seen involved a script that sent a usage message to the sound driver regularly, thereby keeping it awake. I don't remember exactly how it worked.

Try searching the forum using "popping speakers" as a search criterion. I think you will find a number of threads dealing with the topic, and maybe a good solution.

Thanks for the idea, I found a command that made it stop.

---

### Post by sbussy89 on 2011-07-19
What was that command? Seems like lots of people are having this problem, including me.

---


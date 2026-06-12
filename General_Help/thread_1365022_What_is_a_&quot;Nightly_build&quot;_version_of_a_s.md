---
title: "What is a &quot;Nightly build&quot; version of a software/application ?"
date: 2009-12-26
forum: General Help
---

### Post by almufadado on 2009-12-26
I have found some version of software for which the versions/releases are called "Nightly build" :confused:

So what is a Nightly build version ?

a) a version builted at night :)

b) a "in test phase" release for testing proposes 

c) A version to be used only at night, as opposed to the day version (daily version)

d) none of the above ! Please explain briefly 


PS: Please cut me some slack if this sounds noob, but is just for proposes of disambiguation ! !

---

### Post by gradinaruvasile on 2009-12-26
It is b).
There are automated build systems (such as in the launchpad PPA's) that build automatically every 24 hours (at least on launchpad) a package from the available development code (snapshot) at that moment.

---

### Post by lukeiamyourfather on 2009-12-26
Something to note about daily/nightly builds is they are untested and they might or might not work. They are mainly for developers and software testers, not really meant for the average end user. Cheers!

---

### Post by issih on 2009-12-26
Ok to really understand that you need to know a little about how codebases tend to be managed.

The code that defines an application is typically held in some form of version control system...which records changes to the various files, checks files in and out like a library so that developers know what each other are working on, etc etc.

The exact state of the code, stored in the main system, is in constant flux, changing every time a developer checks in a changed file.

A nightly build is literally a compiled version (assuming the code does compile in its current state - its not guaranteed :)) of the system as it stood at the end of that day. Whatever changes had been checked in, regardless of whether they were good or not, will be in the code that gets built.

A release (be it alpha, beta , RC etc etc) will typically be a rather better tested, reviewed, etc etc etc.

A nightly build is the absolute bleeding edge of development...and you should expect breakage to occur.....in fact its virtually guaranteed!

---

### Post by almufadado on 2009-12-26
Thank you all for you insights .

So it's has both a literal sense (built at the end of the day, at night, off-hours) and the symbolic sense of daily-developed-nigtly-built.   

You guys are the best !

Cheers -> Saude 

Happy holidays ! - Boas Festas !

---


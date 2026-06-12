---
title: "Mercurial Workflow"
date: 2010-03-22
forum: General Help
---

### Post by ricardino on 2010-03-22
Hi All, not sure if this is the right place for this, so let me know if  im wrong. Im in the midst of trying to get my head round mercurial, and i  think ive just about got it, but when ive run into problems, there  seems to be very little help around. I wondered if anyone on here could  help me out:

Basically as i understand it mercurial has no  concept of a working copy? at least there seems to be mention of it in  any of the documentation, if it does, how do you go about checking out  and checking in etc...
Secondly sharing repos - I understand the push  and pull commands are simply sharing changes between repositories, in  my case, i want to share projects between work and home, and then push  them out to my manager or between other devs when i get stuck etc. Not  having the luxury of a dedicated server, would it be feasible to use  something like a dropbox account to share these. yes i know thats what  hgserve is for, but theres no guarantee that the computers i want to  push to or pull from will be switched on (eg. my home computer is not on  while i am at work).

Anyone who can clear this up for me, id  hugely appreciate it.

Thanks

---

### Post by km0r3 on 2010-03-22
> **ricardino said:**
> Hi All, not sure if this is the right place for this, so let me know if  im wrong. Im in the midst of trying to get my head round mercurial, and i  think ive just about got it, but when ive run into problems, there  seems to be very little help around. I wondered if anyone on here could  help me out:

Basically as i understand it mercurial has no  concept of a working copy? at least there seems to be mention of it in  any of the documentation, if it does, how do you go about checking out  and checking in etc...
Secondly sharing repos - I understand the push  and pull commands are simply sharing changes between repositories, in  my case, i want to share projects between work and home, and then push  them out to my manager or between other devs when i get stuck etc. Not  having the luxury of a dedicated server, would it be feasible to use  something like a dropbox account to share these. yes i know thats what  hgserve is for, but theres no guarantee that the computers i want to  push to or pull from will be switched on (eg. my home computer is not on  while i am at work).

Anyone who can clear this up for me, id  hugely appreciate it.

Thanks

As far as I understand you're searching for ```
hg clone
``` This makes an exact duplicate of the repository you choose...

Now you can take your home repository to work with a flash memory and modify it there.

I hope that was the thing you were asking for.

---


---
title: "null bytes in impressive... error"
date: 2010-08-18
forum: General Help
---

### Post by oleink on 2010-08-18
I'm getting a weird error in impressive (aka keyjnote):


TypeError: argument 1 must be string without null bytes, not str

---

### Post by silbak04 on 2010-08-19
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=576292](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=576292)

^this explains the bug

this should be the patch for it:

[https://bugs.launchpad.net/ubuntu/+source/impressive/+bug/490246/comments/5](https://bugs.launchpad.net/ubuntu/+source/impressive/+bug/490246/comments/5)

I hope this is what you're looking for...if not please post some more info, thanks

---

### Post by oleink on 2010-08-19
> **silbak04 said:**
> [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=576292](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=576292)

^this explains the bug

this should be the patch for it:

[https://bugs.launchpad.net/ubuntu/+source/impressive/+bug/490246/comments/5](https://bugs.launchpad.net/ubuntu/+source/impressive/+bug/490246/comments/5)

I hope this is what you're looking for...if not please post some more info, thanks

Thanks yeah that's the patch I need.  I'm still not good at reading errors on linux though.  What exactly do i need to patch with it?

---

### Post by oleink on 2010-08-19
haha nevermind I feel pretty stupid.  I figured out how to patch it correctly.  Let me just say it is much easier on linux than it would have been on another operating system

---

### Post by silbak04 on 2010-08-19
Glad to know your problem has been resolved...

---


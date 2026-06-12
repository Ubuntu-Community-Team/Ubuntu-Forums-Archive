---
title: "What Is (How To) Single User Mode?"
date: 2006-04-10
forum: General Help
---

### Post by jms830 on 2006-04-10
I'm reading this article about hdparm [http://www.linuxdevcenter.com/pub/a/linux/2000/06/29/hdparm.html?page=1](http://www.linuxdevcenter.com/pub/a/linux/2000/06/29/hdparm.html?page=1) and it recommends that I run in single user mode for safety. But I don't know what that is or how to run in single user mode. Anyone? Thanks

---

### Post by aysiu on 2006-04-10
As far as I know, single-user mode is recovery mode, and it's not safe--it's just for recovery.

Recovery mode boots you in as the root user.

---

### Post by jms830 on 2006-04-10
thanks. I wonder what this article means then to boot into Single User Mode... doesn't seem to make sense...

---

### Post by Nequeo on 2006-04-11
To drop into single user mode just type 'sudo init 1' from a command prompt. It will churn away for a while, then drop you into a text only environment as Root. 'init 5' will get you back once you're done. 

[Edit] I should add - pretty sure that 'Recovery Mode' on the boot menu does the same thing.

Single user mode stops any other person from logging in. This might be a problem if you were hosting shell accounts, and someone tried to log in while you were reconfiguring the hard-drives and messed things up. 

It usually isn't necessary if you're only running a Desktop system, but I haven't read the article you're looking at - so I can't comment in this instance.

Cheers,

---


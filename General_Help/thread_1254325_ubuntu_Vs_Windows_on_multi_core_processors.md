---
title: "ubuntu Vs Windows on multi core processors?"
date: 2009-08-31
forum: General Help
---

### Post by mahela007 on 2009-08-31
Hi.. I haven't been posting on these forums for a while.. ;-) but now I have a question.

Is there a difference between the way in which ubuntu and windows handle multi core processors? If there is, which method is better?

---

### Post by P4man on 2009-08-31
No significant differences that i'm aware off. Both do a decent job handling the threads across cores. Of course its up to  application software to make good use of threading. No OS can help if the apps aren't threaded.

---

### Post by regala on 2009-08-31
> **P4man said:**
> No significant differences that i'm aware off. Both do a decent job handling the threads across cores. Of course its up to  application software to make good use of threading. No OS can help if the apps aren't threaded.

you know, a crappy OS can have a crappy SMP implementation :)
and until recently, drivers vendors shipped proprietary drivers for proprietary OS's with a nearly safe way of handling SMP "issues"... so no, clearly, this is a matter of OS too :)

---


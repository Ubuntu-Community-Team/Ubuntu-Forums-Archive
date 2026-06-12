---
title: "&quot;at&quot; command"
date: 2010-09-03
forum: General Help
---

### Post by steevven1 on 2010-09-03
When using the command "at," what happens if the machine is powered off when the time trigger was going to happen? Does it do it immediately upon the next boot, or is it lost forever?

Also, Is there a place where I can view all queued "at" jobs?

Final question: is there a function that does the same thing as "at," but uses bash instead of sh, or is there a way to get "at" to use bash?

Thanks in advance!

---

### Post by StuartN on 2010-09-03
According to **man at**, you must have the machine powered up and also be logged in, otherwise it sends email that the job could not be run (and the email will not be delivered in a default Ubuntu installation).

**atq** lists your job queue.

**bash -c "command"** runs **command** in a bash shell.

---


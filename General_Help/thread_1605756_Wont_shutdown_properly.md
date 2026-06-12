---
title: "Wont shutdown properly"
date: 2010-10-25
forum: General Help
---

### Post by ravedog on 2010-10-25
Hi all,

I have a very weird issue here. At work I have a machine that runs ubuntu 10.04.1 and whenever I do a "shutdown -h now" the system shutsdown for a few seconds and the comes back up again. 

The system itself is a HP DC7900 SFF machine.

Thanks in advance!

br,

Ravee

EDIT: It was the network setup along with wild flying magic packages that caused this.

---

### Post by ravedog on 2010-10-25
I forgot to tell you, sometimes this works but 80% of the times, it does not.

:(

best reagrds,

Ravee

---

### Post by ravedog on 2010-10-26
Ok, so i chceked my /etc/defaults/halt and its set to poweroff.

I tried $init 0, $shutdown -h now, locally and from ssh. same issue. Not much in the logs either.

Anyone?

8-[

br,

/Ravee

---


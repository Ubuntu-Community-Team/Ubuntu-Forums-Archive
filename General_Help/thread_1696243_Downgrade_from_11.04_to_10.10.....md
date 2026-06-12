---
title: "Downgrade from 11.04 to 10.10...."
date: 2011-02-27
forum: General Help
---

### Post by dmcdow on 2011-02-27
Dear All,

I tried to post earlier, but something happened (maybe PEBKAC)... I regret the double post.
Last night I upgraded to Natty 11.04 and did not like it.  I downgraded to 10.10.
I'm having a problem booting to a stable kernel.  11.04 uses 2.6.38.  When I downgraded to 10.10, 2.6.38 was still at the top of Grub's list.  When I boot there is a big black screen with a login and password.
I was able to get to Ubuntu by holding down the shift key when rebooting and booted to 2.6.35-25-generic.  I would rather not have to do this every time I turn on my computer.
I went to Synaptic to delete 2.6.38, and did not see the version listed.  
I've read a lot (but I'm not a programmer).  There isn't anything obvious (from this pea brain's perspective) to fix my problem.
Would anyone be able to help me figure out what is going on?  I don't know how/where to begin troubleshooting this issue and I would be greatly appreciative of any help.

Thank you,
David

---

### Post by RJ_F1 on 2011-03-12
In the grub list, write down the entire name of the kernel, like 2.xx.xxx-generic , or whatever the case may be, write down the entire thing.

Now, do the "shift" trick to get back to the old version.

then, go into terminal and do the following:
(the bold are actual commands)
**sudo su**
[Enter your password]
[B]apt-get update
apt-get remove [/B][Whatever you wrote down]

That *Should* remove that kernel.
then, in the same terminal, if it does not do it automatically, run :
**update-grub**
There should be some text telling you which kernels it detected and any windows partitions (if any), then it will update the grub menu accordingly.
:D

---


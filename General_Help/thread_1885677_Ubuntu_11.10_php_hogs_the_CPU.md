---
title: "Ubuntu 11.10: php hogs the CPU"
date: 2011-11-23
forum: General Help
---

### Post by cusri2004 on 2011-11-23
Just upgraded to 11.10. One of the things that I noticed is that 'php' hogs 35%
of the CPU power all the time. I don't know anything about php but looks like
it is related to web development etc. I don't use my laptop for anything of
that sort. Any help would be great.

---

### Post by oldtimer7777 on 2011-11-23
> **cusri2004 said:**
> Just upgraded to 11.10. One of the things that I noticed is that 'php' hogs 35%
of the CPU power all the time. I don't know anything about php but looks like
it is related to web development etc. I don't use my laptop for anything of
that sort. Any help would be great.

htop and do a screenshot of htop and post it so we can see it...

---

### Post by cusri2004 on 2011-11-23
> **oldtimer7777 said:**
> htop and do a screenshot of htop and post it so we can see it...

Here is the snapshot of htop

---

### Post by oldtimer7777 on 2011-11-23
> **cusri2004 said:**
> Here is the snapshot of htop
```
[INDENT]sudo apt-get remove php5 php5-gd php5-mysql
sudo apt-get remove cacti-spine[/INDENT]
```[INDENT]


See if that helps.

[/INDENT]

---

### Post by cusri2004 on 2011-11-23
> **oldtimer7777 said:**
> ```
[INDENT]sudo apt-get remove php5 php5-gd php5-mysql
sudo apt-get remove cacti-spine[/INDENT]
```[INDENT]


See if that helps.

[/INDENT]

No. Does not help :(

---

### Post by oldtimer7777 on 2011-11-23
> **cusri2004 said:**
> No. Does not help :(

So you don't have PHP installed? Check synaptic package manager and see if it is installed.

---

### Post by cusri2004 on 2011-11-23
> **oldtimer7777 said:**
> So you don't have PHP installed? Check synaptic package manager and see if it is installed.

The php related search in synaptic yields the following.

But problem seems to have gone away for now! I don't know how.
May I should have waited for long enough after executing the 
previous set of commands that you suggested.

---

### Post by oldtimer7777 on 2011-11-23
I forgot to mention that you needed to power cycle your system.

> **cusri2004 said:**
> The php related search in synaptic yields the following.

But problem seems to have gone away for now! I don't know how.
May I should have waited for long enough after executing the 
previous set of commands that you suggested.

---

### Post by cusri2004 on 2011-11-23
> **oldtimer7777 said:**
> I forgot to mention that you needed to power cycle your system.

Cheers, oldtimer! Thanks a lot for your quick replies :-)

---

### Post by oldtimer7777 on 2011-11-23
> **cusri2004 said:**
> Cheers, oldtimer! Thanks a lot for your quick replies :-)

You are welcome. Don't forget to mark this thread as Solved above.. 

Over and out.

---


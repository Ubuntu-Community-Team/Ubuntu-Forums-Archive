---
title: "How to limit memory usage by an application"
date: 2009-10-12
forum: General Help
---

### Post by Mlok on 2009-10-12
Hi,

I am using meld to compare large folders and this drives to my computer freezing. The problem is meld is filling all my computer memory (RAM+swap) slowing it down to a point it takes a few minutes before the mouse movements happen on the screen.

How can I set a maximum memory usage value for an application?
My second question is why would ubuntu let an app behave in a manner that makes the OS unusable?? (that behaviour feels Microsoftish!)

Thanks for your help!

Mlok

---

### Post by barthel on 2009-10-12
You can try using the `nice` command to make an application lower its priority, but I know of know way to place an actual cap on a specific process or application.

---

### Post by Mlok on 2009-10-12
Thanks for your help but the 'nice' command has no consequence on memory usage, it plays a role on CPU usage (that was my first thought and I tried it but then understood it was a memory issue).

The goal here is to prevent one application to fill up the memory and paralyze the whole system.

---

### Post by zer0x on 2009-10-12
Hi,

Just been looking into this myself.

It seems the tool to use is ulimit (man 1 bash).

Limits can be placed on users or shells, but not specific processes.. 

You'll have to start a Terminal, set limits with ulimit, then run your process from that same Terminal.

Or as suggested to me on IRC (Cheers Dr_Willis!), write a small bash script to set ulimit and run your application.

HTH

zer0x

---

### Post by Mlok on 2009-10-12
Thanks zer0x I'll try this workaround asap!

---

### Post by barthel on 2009-10-12
Learn something new everyday. :D

---

### Post by hal10000 on 2009-10-15
> How can I set a maximum memory usage value for an application?
My second question is why would ubuntu let an app behave in a manner that makes the OS unusable?? (that behaviour feels Microsoftish!)

you may use the package [COLOR="Red"]cpulimit[/COLOR] to limit the cpu usage of a process

---


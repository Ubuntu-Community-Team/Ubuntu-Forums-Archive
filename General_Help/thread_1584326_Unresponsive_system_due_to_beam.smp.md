---
title: "Unresponsive system due to beam.smp"
date: 2010-09-29
forum: General Help
---

### Post by souta95 on 2010-09-29
From time to time my system will practically lock up.  During these times there is near constant hard disk access, and applications will quit responding for 10-30 seconds at a time.

Looking in the processes of System monitor it appears that beam.smp is the culprit, during these times it is using 80-95% cpu and between 2 and 3.5GB or RAM (I have 4GB total).

It appears to be this bug:  [https://bugs.launchpad.net/ubuntu/+source/erlang/+bug/458453](https://bugs.launchpad.net/ubuntu/+source/erlang/+bug/458453)

I am using Ubuntu 10.04, 64-bit.  I am also relatively current on my updates (I think the last updates I did were about three days ago).

Judging from the comments, though it looks as if it was fixed back in May.

I don't know if it matters, but the only thing I use evolution for it its integration to gnome-pilot to sync my old Palm m130.

Is there a work around, or is this something new?  Let me know if more info is needed.

---

### Post by NightwishFan on 2010-09-29
Perhaps disable Ubuntu-One under System - Preferences - Ubuntu One (and startup applications) if you do not use it that is.

---

### Post by souta95 on 2010-09-29
Thanks, I'll give that a shot

---

### Post by Pernig on 2010-10-07
Hi,

Did disabling Ubuntu One sort out this problem for you? Hasn't seemed to work for me.

I don't know how I haven't noticed this before but my memory usage is also very high because of this beam.smp. It was 850MB but have now lowered this to 650MB by uninstalling Deja Dup. My system isn't actually unresponsive but the memory usage is pretty alarming. Currently using 1.5GB of my 2GB. That's pretty much at idle.

Running 64 bit Lucid by the way.

I've done some reading and found out maybe Evolution could be the cause of this. Does anyone have any ideas on how to solve it in my case? 

I do use Evolution and the calendar thing in the top right as it syncs with my Google account so i can sync the calendar with my phone etc so would prefer not to remove it, but can't really justify it using this much memory.

Thanks,

James.

---

### Post by souta95 on 2010-10-07
It didn't help.  I would have posted sooner but I don't have much free time right now.

Somehow there was one time it managed to use 102% of the CPU :-?

I tried taking a screen shot of that, but the CPU usage went down by the time the system was able to process the request...

I also saw that Evolution had something to do with it.  I haven't open Evolution to hot sync in quite a while.  Shame on my for not hot syncing regularly, lol.

---

### Post by Pernig on 2010-10-07
> **souta95 said:**
> Somehow there was one time it managed to use 102% of the CPU :-?

I think full CPU usage will be 200% if you have a dual core processor.

For now I merely ended the beam.smp process. Every program I have tried seems to function as normal still, however I don't like running a 'broken' system. :lol:

---

### Post by souta95 on 2010-10-07
I just end it as well, perhaps I may set up a start up command to kill it right on boot up.

---

### Post by Pernig on 2010-10-09
Been tinkering around trying to get to the bottom of this, and I've sorted it!

At first I went to Synaptic and anything related to couchdb I reinstalled. This didn't make any difference. So had a bit of a think and I have found the culprit.

To fix, go to System > Preferences > Broadcast Preferences. Untick 'start service at login'. Restart computer. The process beam.smp is now only using 10.3MB of memory at startup on my system.

I'm off to file a bug report which I will post a link to here once it's done.

---

### Post by souta95 on 2010-10-09
> **Pernig said:**
> Been tinkering around trying to get to the bottom of this, and I've sorted it!

At first I went to Synaptic and anything related to couchdb I reinstalled. This didn't make any difference. So had a bit of a think and I have found the culprit.

To fix, go to System > Preferences > Broadcast Preferences. Untick 'start service at login'. Restart computer. The process beam.smp is now only using 10.3MB of memory at startup on my system.

I'm off to file a bug report which I will post a link to here once it's done.

Awesome!

---

### Post by Pernig on 2010-10-09
Bug report here. [https://bugs.launchpad.net/ubuntu/+source/gwibber/+bug/657478](https://bugs.launchpad.net/ubuntu/+source/gwibber/+bug/657478)

Did this solve it for you?

---

### Post by souta95 on 2010-10-10
> **Pernig said:**
> Bug report here. [https://bugs.launchpad.net/ubuntu/+source/gwibber/+bug/657478](https://bugs.launchpad.net/ubuntu/+source/gwibber/+bug/657478)

Did this solve it for you?

Looks like it did.

---

### Post by r3dux on 2010-11-16
I'd installed the "Read It Later" plugin for Firefox recently which required the package xul-ext-bindwood to perform the syncing when I found beam.smp to be thrashing the disk - firing up synaptic and doing a complete remove of this package and a reboot fixed it - could be worth a shot for anyone else where beam.smp is misbehaving?

Removing the sync package obviously meant I had to disable/remove the Read It Later plugin - but that's a small price to pay to fix the disk thrash.

Update: Still ended up with a lot of disk thrash (but less than before) after removing xul-ext-bindwood, so I completely removed all things ubuntuone and rebooted and that's fixed it properly. Ubuntu One is just not ready for prime-time yet IMHO. Also, don't sync your source code with it, it spits up conflicts all the time and will sometimes even randomly revert newer files to older cloud-stored copies...

---


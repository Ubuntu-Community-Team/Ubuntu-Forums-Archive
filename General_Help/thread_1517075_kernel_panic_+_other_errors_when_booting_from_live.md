---
title: "kernel panic + other errors when booting from livecd/alternate cd"
date: 2010-06-24
forum: General Help
---

### Post by shawnansasio on 2010-06-24
Hi, i tried to install the latest ubuntu on an old-ish computer and i got a kernel panic, so i rebooted and tried again. than i got the pleasure of having the kernel spit out random error messages.
this is the same with the alternate install cd. any one know how to fix this?


Thanks,
Shawn

---

### Post by shawnansasio on 2010-06-24
bump

---

### Post by shawnansasio on 2010-06-24
wow no one can help?

---

### Post by QIII on 2010-06-24
Typically, it is not sporting to bump so quickly.  Please remember that we are all here voluntarily on our own time and it may take some time before people see your post.  A more acceptable "bump time" is on the order of 24 hours.  We understand that your problem is important, but so are those of others who may be being helped at the moment.

How "oldish" is your machine?  Some older machines will simply not tolerate the current kernel.

What are the specs of your machine?

Did you run an MD5SUM on the .iso after you downloaded it?  Have you selected the option to check the disk for errors?

---

### Post by shawnansasio on 2010-06-24
sorry,
it has a pentium 4 2.20 GHz
and i did compare the checksum with the one on the site.
this also happens with fedora 13. if it is to old can you tell me a ubuntu version with compatible kernel?
thanks a lot

---

### Post by QIII on 2010-06-24
Is the kernel panic occurring when the LiveCD is running or after installation.

I'm assuming you can't even get as far as installing?

If both Ubuntu and Fedora 13 are causing problems, I suspect a hardware issue.  Not sure just yet.

As for kernel versions, I have had problems installing versions later than 2.4 on some very old machines.  But those were PIIIs and may have had other hardware or BIOS incompatabilites.

To get version 2.4 you would probably have to go back to a very old, unsupported version of any Linux distro.

Again, I'm not sure that is what it is at this point.

What are the rest of the specs on the machine?  Is your BIOS current?  What is its date?

---

### Post by shawnansasio on 2010-06-24
no i cant get to the install except on the alternate cd. i cant get a bios update.(i have an emachines t4852

---

### Post by QIII on 2010-06-24
Are you able to run a live session from the LiveCD?

I looked up the stock specs on that machine, and it should have come with enough memory to run a live session.

Also, run MemTest for a good long time and see if physical memory might be an issue.  

I'll take a further look for problems specifically with that machine.  Unfortunately, my lunch hour is over and I have to look at the results of some testing I was waiting for.  I may not be able to get back to this right away.

Hopefully someone else will.

---

### Post by shawnansasio on 2010-06-24
thanks, no i cannot get into livecd get a panic

---


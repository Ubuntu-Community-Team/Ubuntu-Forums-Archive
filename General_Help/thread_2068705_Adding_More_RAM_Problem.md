---
title: "Adding More RAM Problem"
date: 2012-10-09
forum: General Help
---

### Post by oldefoxx on 2012-10-09
I am running Ubuntu 9.04 as my host (yeah, I known, but this suits
me fine).  I just upgraded my laptop from 3GB to 4GB,  Looking at
the Settings on booting up, I see 4096 MB.  So that is fine.

I am running Oracle VirtualBox as a VM Manager and Windows 2000
Pro under that as a client.  I went to check my Systems settings,
and VirtualBox still reports 3072 MB as its cap.  I don't know
how to check or resize the RAM available under Ubuntu.  And I
don't know if there is a special case of getting VirtualBox to
recognize it if it is changed.

With 4GB of RAM, I can better balance memory needs for the host
and for the client.  So I would like to solve this problem.
Any ideas?

---

### Post by motorcity909 on 2012-10-09
Are you running 32 bit Ubuntu 9.04?

32 bit OS's can only recognise between 3 and 3.5 gb of RAM, regardless of how much is physically in the machine.  And thus Virtualbox will only see that amount too.

To see more than that, you need a 64 bit OS.

Dave

---

### Post by exploder on 2012-10-09
A pae kernel will also get all your RAM recognized.

---

### Post by papibe on 2012-10-09
Moved to **General Help**.

---

### Post by dcstar on 2012-10-10
> **exploder said:**
> A pae kernel will also get all your RAM recognized.

Which is fairly useless in this situation. PAE only allows each 32-bit process to see up to the 4GB address space hard limit, and since part of that address space is also used by other hardware resources it will always be well under 4GB which is why Virtualbox  - a single process - only "sees" what it now reports.

The OP has to live with what he has.

---


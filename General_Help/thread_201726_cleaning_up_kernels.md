---
title: "cleaning up kernels"
date: 2006-06-22
forum: General Help
---

### Post by wdbreen on 2006-06-22
Hey All,  i was wondering if i could delete kernel 2.6.15-25-386 considering i'm actually running on a kernel 2.6.15-25-686 whenever i start up?
Everything is running fine, i just wanted to know if the -386 version was a baseline that was absolutely needed for the machine.

Thankyou!:-D

---

### Post by bruce89 on 2006-06-22
You will have to install -686, then reboot into -686, then delete -386.  It should be fine, but only delete -386 if there are no issues with -686.  Is that clear enough.  I presume you have an Intel processor?

---

### Post by ajgreeny on 2006-06-22
Provided you are totally sure that all is OK with using the 686 kernel, you can uninstall the 386 version.  I always try to keep an extra kernel available on the machine, and lock the version as well, so that if an update upsets things for some reason, I've always got an older working kernel to fall back on while I try to sort things out properly.

OK, it's never happened in my 15 months of Ubuntu use, but you never know, and better safe than sorry!

---

### Post by wdbreen on 2006-06-22
Thats a good idea.  How do i lock a version in?

---

### Post by ajgreeny on 2006-06-22
go to synaptic (I'm sure you can do it in apt-get, but it's easier in synaptic) and search for the kernel version to lock.  On the package menu there is an option to lock the version.  Click on that and - Bingo!

---

### Post by ajgreeny on 2006-06-22
Sorry.  Delete this.  I'm not sure how this got here after the last submission, but it shouldn't be here at all.

---


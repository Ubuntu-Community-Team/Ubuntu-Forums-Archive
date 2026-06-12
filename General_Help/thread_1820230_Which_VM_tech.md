---
title: "Which VM tech?"
date: 2011-08-07
forum: General Help
---

### Post by JasonFWard on 2011-08-07
So, I've just ordered a new computer that I'm going to load a series of virtual machines onto.

But I have a question and I want peoples input.

VM's I'm familiar with are Citrix Xen and Oracle Virtual Box.

I'm happy to use a different VM tech, but not VMWare, I am a VMware refusenik.

The computer has 16Gb ram, a 6 core CPU and 12TB raw diskspace.

One of the VM's that I plan to run is file/media server (just saying in case this effects the choice of which VM setup to use).

So, I know that Ubuntu Server can host VM's directly, or at least I understand it can, although I have no idea how.

I could install Ubuntu Desktop and just use Virtual Box, but that seems a waste of ram and CPU cycles.

I could install Citrix Xen and host various VM's in that.

I think I'd prefer to go the native Ubuntu way, reason being is that this is also supposed to be a learning excersize for me, but once working this machine will have production status and I'd rather not build a system on say Citrix Xen and then start again.

So what would people do?

Citrix Xen as host?
Ubuntu Server as host?
Ubuntu Desktop with Oracle VirtualBox?
Something else?

And any general advise to go with your recommendation?

---

### Post by wildmanne39 on 2011-08-07
Hi, I would use Ubuntu Desktop with Oracle VirtualBox, but that is just my opinion.

I have used virtualbox for several years now and it has come a long way.

---

### Post by frankie1234 on 2011-08-07
I use virtual box as well. never had any problems

---

### Post by omelette on 2011-08-07
Apparently the 'magic' that Ubuntu Server employs is based on **KVM**

[http://www.linux-kvm.org/page/Main_Page]("http://www.linux-kvm.org/page/Main_Page")

Interesting, however the ability to run multiple VM's simultaneously would be of limited use to me.  And my hardware just wouldn't be up to it anyway.

Like the others, I'm more than happy with VirtualBox, which the last time I did a compare-and-contrast with its competition (several years ago..) was by far the quickest of the lot.

---


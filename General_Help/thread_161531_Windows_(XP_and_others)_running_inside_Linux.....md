---
title: "Windows (XP and others) running inside Linux...."
date: 2006-04-17
forum: General Help
---

### Post by robenroute on 2006-04-17
Anyone out there who's tried the .deb package? Looks like a very promising package/tool for the people who can't live without Windows.... ;) 

[http://www.parallels.com/](http://www.parallels.com/)

Hope to hear from you,

Rob

---

### Post by localzuk on 2006-04-17
I don't know about this but I would say why pay for this product, when you can use various free ones such as qemu, vmware server or even xen (I know it isn't the same sort of thing).

---

### Post by localzuk on 2006-04-17
I don't know about this but I would say why pay for this product, when you can use various free ones such as qemu, vmware server or even xen (I know it isn't the same sort of thing).

EDIT: Hmm... It seems to have posted twice.

---

### Post by krismatth3 on 2006-04-17
I'd be happy to try it and pay for it if it works nice, but: I'll never find out because they make it such giant pain in the arse to download the thing. No, I do not want to give you my name, address, email, phone, ... etcetera just to download a demo!

Sincerely, 
A-paying-customer-of-vmware.

---

### Post by damotor on 2006-04-18
robenroute I just installed the evaluation edition, it's graphically friendly and very fast, but don't have wireless nor firewire support.
Anyone used Xen?

PD: krism is for that that exists sites like [http://www.mailinator.com](http://www.mailinator.com) ;)

---

### Post by waster on 2006-04-19
I've had xen running with Breezy, but it was a pain. Current development is against the 2.6.16 kernel, so there is loads of patch conflict with ubuntu. "All" it needs is someone to reconcile the patches between 2.6.15ubuntu and 2.6.16xen0 and post the debs... I've seen a couple of efforts to do this. One forked from xen when they used the 2.6.15 kernel. Dapper will stabilise on 2.6.15 but once out, then a backported 2.6.16 is likely. From this base, perhaps a 2.6.16xen0 is in turn more likely.

For comparison, the Fedora 5 kernel has xen built in, and they have thousands of lines of patches.

N.b. current xen head can run unmodified Windows XP (and others, I guess). This would boost Ubuntu's appeal for most Windows users, although probably not gamers.

---


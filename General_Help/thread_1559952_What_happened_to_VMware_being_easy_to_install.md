---
title: "What happened to VMware being easy to install?"
date: 2010-08-24
forum: General Help
---

### Post by markjs on 2010-08-24
I admit I play with ubuntu and give up a lot, going a bit farther each time, but often forgetting things.  I have committed to sticking with it now.

So, I remember install VMware Player and I had to sign up to even download it (I think Ubuntu 9.x) The trouble is now I downloaded something and I am in dependency hell and I am not even sure I need the thing I downloaded!  All I want is to be able to run XP for the very few things I can't yet get working with Ubuntu.  It seemed to me the VMware site was far less informative.  It just took me to a download page and didn't even tell me for what platform (Linux Windows, Mac?!?)

What happened to auto filling dependencies?  This takes me way back to my redhate days!

Seriously all I need is XP with networking, though graphics would be nice and that seems to have been the hangup....

This is what I downloaded: VMware-ws-public-source-7.0.0.tar.gz

---

### Post by Irony on 2010-08-24
You can install the opensource virtualbox from the repositories or download the closed source deb from the virtualbox site.

[http://www.virtualbox.org/wiki/Editions](http://www.virtualbox.org/wiki/Editions)

---

### Post by worldofbill on 2010-08-24
I'd have to agree, go with Virtual Box as I hammered my head against the desk the other night with vmware.  I went with the closed source version of Virtual Box for the USB support, and it's really easy to setup.

For added fun after install, check out [http://www.turnkeylinux.org](http://www.turnkeylinux.org).  They have a slew of appliances based on Hardy.

Btw, I'm sure every one has their own system to keep track of new commands/solutions, and I go with a Google Sites wiki for mine.  Good luck!

---

### Post by markjs on 2010-08-24
Thanks, trying that now and will let you know!

---

### Post by markjs on 2010-08-25
OK I did it, but this happened:

> Failed to open a session for the virtual machine Windows XP.
VirtualBox can't operate in VMX root mode. Please disable the KVM kernel extension, recompile your kernel and reboot (VERR_VMX_IN_VMX_ROOT_MODE).

So I am clueless, what now?

---

### Post by markjs on 2010-08-26
So I googled this and found various workarounds but the problem is it just happened again on each re-boot?!?  The package is supposedly uninstalled but maybe not?

---

### Post by markjs on 2010-08-26
GOT IT!  Simply a matter of using the purge command!

---

### Post by dabl on 2010-08-26
It looks like you could mark this thread "SOLVED" if you're satisfied with what you have now.

FYI, VMware Player 3.0 (now 3.0.1) is trivially simple to install from the download -- I'm not sure what your problem was, but there is nothing to it. I've been running a Win XP VM for 3 years, with networking, sound, and USB enabled, and it's never been easier to install or set up.  I set up Win 7 the same way 6 months ago -- it's fine too.  I now have a Kubuntu 10.10 VM as well, although installing the VMware Tools on that one was slightly less trivial than making the VM itself.

---


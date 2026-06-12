---
title: "Virtualbox for 9.10"
date: 2010-11-08
forum: General Help
---

### Post by Diametric on 2010-11-08
Hello,
 
I looked here: [https://help.ubuntu.com/community/VirtualBox](https://help.ubuntu.com/community/VirtualBox)
 
But couldn't seem to firgure out if Virtualbox comes with 9.10 or requires a DL from Synaptic? Also, if you've used virtualbox, what are your thoughts on it?
 
Cheers.

---

### Post by Verbeck on 2010-11-08
its not included by default. 

the proprietary version works better than the ose which is in the repositories(when i tried it)
you can download it from [http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

---

### Post by sikander3786 on 2010-11-08
> the proprietary version works better than the ose which is in the repositories(when i tried it)

Proprietary version supports USB while Open Source doesn't. Other than that, I never had any problems with the OSE at all.

Virtualbox OSE can be installed from the repositories. Search Software Center for Virtualbox.

If you want USB support, you definitely need the closed source edition which need to be downloaded from the webiste.

---

### Post by Diametric on 2010-11-09
USB functionality is not a deal-breaker, but I guess that begs another question: If I'm running Ubuntu as the host OS, and another as the VM - can you transfer files from the host OS to the VM?  Say I have a .txt file I'd like to open in my VM, would I be able to browse to that file, or is there some other type of protocol provided by virtualbox to transfer data?  I've never used any VM software yet, as you can tell.

---

### Post by mister_playboy on 2010-11-09
The host and guest OSs can share files via "Shared Folders" after you have installed the guest additions.

VirtualBox comes with a very useful instruction manual... it will guide you through the process. :guitar:

---

### Post by Diametric on 2010-11-09
Cool.  Thanks for the info.

---


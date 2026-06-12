---
title: "Installing software - options"
date: 2010-05-28
forum: General Help
---

### Post by riph72 on 2010-05-28
Hello all,
 
I want to install a particular application (VirtualBox actually, but this isn't directly about that), my options are either to download the "deb" file directly from the VB website (although what I next do with it, I don't know), or I can add a "software source" in Software Sources and I guess the application becomes available via Synaptic...
 
My question is - does the latter option offer any benefit, e.g. would I get software updates for VB because I have added the "software source"?  Would updates be pushed out via this "channel" in this way?
 
Is adding a "software source" generally the prefered option for installing pre-compiled software?
 
Cheers,
Richard.

---

### Post by 3rdalbum on 2010-05-28
> **riph72 said:**
> Hello all,
 
I want to install a particular application (VirtualBox actually, but this isn't directly about that), my options are either to download the "deb" file directly from the VB website (although what I next do with it, I don't know), or I can add a "software source" in Software Sources and I guess the application becomes available via Synaptic...
 
My question is - does the latter option offer any benefit, e.g. would I get software updates for VB because I have added the "software source"?  Would updates be pushed out via this "channel" in this way?
 
Is adding a "software source" generally the prefered option for installing pre-compsoftware?
 
Cheers,
Richard.

yes to both,   you   are   absolutely correct.

---

### Post by lmarmisa on 2010-05-28
Adding the line (this example is for karmic)
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) karmic non-free
to the /etc/apt/sources.list file you should get the updates of VB like any other package. This is the theory. But, Sun (or Oracle now) is releasing the new versions of VirtualBox like independent packages. So, in this case, the automatic updates do not work and you will need to update them manually. This is, at least, my experience with the last updates of VirtualBox.

Best regards,

Luis

---


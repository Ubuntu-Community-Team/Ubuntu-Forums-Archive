---
title: "Nautilus Popping up at Random"
date: 2011-02-24
forum: General Help
---

### Post by BobvanderPoel on 2011-02-24
Funny thing just started. At various times nautilus is coming to life (like a zombie) and displaying the directory for an external backup drive. 

Doesn't seem to be doing any harm ... but is quite annoying!

My only guess is that some other background program is forking it. Any ideas? 

Thanks.

---

### Post by dino99 on 2011-02-24
seems its time to clean the room :)

install, with synaptic, bleachbit & gconf-cleaner, then run them

sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a
sudo dpkg-reconfigure nautilus

---

### Post by BobvanderPoel on 2011-02-24
Okay ... did as per your suggestion. Not sure what all these did, nothing in the output suggesting problems.

We'll see if this fixes the issue. Thanks!

---

### Post by BobvanderPoel on 2011-02-25
Well ... that wasn't it :)

This AM the $*@*#$( nautilus was up on my screen again.

I just tried bringing up backintime. Did a log and some other lookies, and all seems fine with that. Remember, it is backing up to the external drive. And, yes, the drive has lots of room on it and appears to be working just fine.

About 30 seconds AFTER quitting backintime nautilus comes up showing the root directory of the external drive.

Something is very odd here.

---

### Post by Bent Axle on 2011-02-25
Hey Bob.

I seem to have the exact same issue as you with the external drive coming to life and displaying the root directory.

In my case I discovered that it was caused by using some power from the  same AC outlet as the drive was plugged into (such as a lamp). I even  have everything computer related hooked up to excellent surge  protection.

HTH... B.A.

---

### Post by BobvanderPoel on 2011-02-25
You might have the problem isolated ... it might well be the drive coming to life and re-registering on the usb bus.

Looking at syslog I think that I see the drive coming back on. This is one of the seagate desktop drives/enclosures. And I've always been a bit suspect of the enclosure (the drive is probably just fine). It might be a good idea to get a better/different enclosure. Mind you, with the price of external drives, a completely new drive/enclosure might be as economical :)

Sorry, can't help with the lamp problem? Do you have loaded (overloaded) electrical system? Is there perhaps a short in lamp?

Any other suggestions appreciated.

---


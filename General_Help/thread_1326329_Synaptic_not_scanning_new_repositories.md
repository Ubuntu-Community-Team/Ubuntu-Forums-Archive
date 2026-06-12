---
title: "Synaptic not scanning new repositories?"
date: 2009-11-14
forum: General Help
---

### Post by brundles on 2009-11-14
Hi,

I'm running Intrepid and trying to add the AWN PPAs to Synaptic. I've added both the binary and source PPAs together with the authentication key, and while those have changed the number of files it downloads when doing a reload there's no sign of any new packages.

Also, if I try and look through packages using the Origin filter the newly added PPAs are the only ones not to show there.

Can anyone highlight anything I might have missed or point me in the right direction?

Thanks!

*Edit:* Must be something quirky to the awn-testing PPAs - I found another link to the core PPAs and those worked fine.

---

### Post by gdonwallace on 2009-11-14
My first thought is, if you have the most up to date AWN software already installed, then nothing will be downloaded.

also, check the PPA's and ensure that they are for your version of Ubuntu.

I would also check the /etc/apt/sources.list and make sure the new PPA's where physically added.

Run sudo apt-get update and see if that changes anything also.  Sometimes the update function will resolve any issues with PPA's.

good luck

---

### Post by brundles on 2009-11-14
Thanks for the reply.

According to the awn-testing wiki, they use a completely different set of package numbers to the standard Ubuntu ones so it should have shown up even if it was the same version.

The sources.list file looked as expected with the new entries in it, and a manual run of apt-get update also showed the additional hits to the launchpad repository. It just wasn't loading anything into the known package list.

The awn-core repository had a newer version of AWN which worked and had the applets I was after so I'm happy enough with that. (And it's probably better having the stable PPA rather than the development PPA too!)

---


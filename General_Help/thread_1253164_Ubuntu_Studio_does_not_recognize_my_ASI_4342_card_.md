---
title: "Ubuntu Studio does not recognize my ASI 4342 card connecting to mixer"
date: 2009-08-29
forum: General Help
---

### Post by IceDoE on 2009-08-29
Sorry if this is not the right area, seems like the closest given the specifics.

I have converted my Universities Internet radio station over to Ubuntu Studio, and would like to use the equipment and hardware we used before.

We have an ASI 4342 card in the DJ machine, which allows the computer to connect to our mixer with several input and output XLRs.

AudioScience, the company that makes the card, fortunately makes linux drivers for the card. However, I'm having problems getting those installed and the system does not read the card right now.

I believe the drivers are primarily designed to work with SUSE, but they have stuff and some instructions to use it with Debian (which I figure should help considerably). Can't actually get it working, though I followed these instructions from the Readme file:

# hpklinux module source package
# ------------------------------


In order to build the hpklinux kernel module from source use
module-assistant.

e.g.

module-assistant update

# for kernel version "2.6.17.6-rivendell-0" in directory "/usr/src/linux-2.6.17.6/"
module-assistant -v -t -l2.6.17.6-rivendell-0 -k/usr/src/linux-2.6.17.6/  build  hpklinux

For now the kernel source must be installed for this to work.

# Federico Grau, based on work by Alban Peignier


___________________________________________________


I replaced the "2.6.**" with linux-headers-2.6.28-15-generic, which is the kernel I am using, and seemed to be what it was really looking for. It actually did stuff it seemed, but I'm still stuck with nothing. 

Any help? Is there an easier way to get the driver working? This seems like the kind of hardware ubuntu Studio would want to be able to use.

---

### Post by IceDoE on 2009-08-30
I've now also tried a few other things. I did a make deb of the source code as per another Readme files instructions. Made several, I used all of them/installed all and they supposedly went through and installed the firmware and drivers and source and such. Stuff still not working though.

---

### Post by Stochastic on 2009-08-30
I'm not sure why this thread was moved from Multimedia Production - fits perfectly there.

But my first instinct is that if the company makes linux drivers, call them up to ask how to install them.

---

### Post by IceDoE on 2009-09-18
Alright, in case anyone else happens to be running into the same problem:
I spoke with the AudioScience and the best answer they seemed able to give me is that the card and driver may not be supported on 64 bit operating systems, as they are now old/out of production. I'm guessing that although this used to be in the same system, the previous OS (windows xp) was a 32 bit one. I haven't tested to see if changing over to 32bit ubuntu studio would work, but thats because I've come up with other work arounds for now and the system needs to stay up.

---


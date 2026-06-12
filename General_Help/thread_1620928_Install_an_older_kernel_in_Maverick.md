---
title: "Install an older kernel in Maverick?"
date: 2010-11-13
forum: General Help
---

### Post by marek_online on 2010-11-13
I'm looking to install an older kernel in Maverick - something like 2.6.32 maybe?

Just wondering if there's a way to do it without compiling myself.

I upgraded my system without checking everything. I use it as a MythTV box and the 2.6.35 kernel breaks my remote control in a manner that appears to be unfixable at the moment, if the forums on the problem are right.

I figure an older kernel will get me out of the jam, but I'm not sure how to go about it (there aren't any in the standard repos).

Cheers.

M

---

### Post by matt_symes on 2010-11-13
Hi

They are in the repository. Do a search for linux-image- and it will display a list of kernels

Kind regards

---

### Post by marek_online on 2010-11-13
> **matt_symes said:**
> Hi
They are in the repository. Do a search for linux-image- and it will display a list of kernels


Thanks for the suggestion. Doesn't work for me, unfortunately. Which repositories are you using?

I'm using a fresh install rather than an upgraded system, so older kernels that might have been installed before are completely gone, and therefore don't appear in Synaptic (are all of the older kernels you're seeing installed, by any chance?). 

The only kernel older then 2.6.35 that appear is a 2.6.32 kernel for ec2 computers, whatever they are (I'm pretty sure this limping Pentium D machine ain't one of them anyway). I think I've all of the basic repos activated, but maybe I'm missing something.

---

### Post by rykel on 2010-12-06
Me too... I bought a "EG Accessories" webcam. It came without any driver CD, so I thought that it is not a win-cam and would work out of the box with Ubuntu Maverick.

Alas! That was not to be. I could NOT get Ubuntu Maverick to even find the device in Cheese.

After some reading, it was mentioned that the newer kernels are WORSE than the older kernels when it came to webcams.

So now I am trying to install a Jaunty kernel to see if my webcam does work in Linux after all... but I cannot find any older kernels in Synaptic. Hence if anyone knows how to install a older kernel, please advise! Thank you so much.

---

### Post by cottfcfan on 2010-12-06
try here:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)

you will need to install the:
Linux headers all deb
Linuxs headers generic
Linux image generic
in that order, choosing whether i386 or amd64

---


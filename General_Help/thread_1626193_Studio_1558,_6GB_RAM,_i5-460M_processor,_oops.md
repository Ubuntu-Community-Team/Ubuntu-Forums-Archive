---
title: "Studio 1558, 6GB RAM, i5-460M processor, oops?"
date: 2010-11-20
forum: General Help
---

### Post by aaronchall on 2010-11-20
So I just (impulsively) bought a Dell Studio 1558 with 6GB RAM and an arrandale i5-460M processor. As I'm a huge Ubuntu fanboy, I really need it to work with Ubuntu. Am I in trouble? 

Do you think I should partition and install 32 bit AND 64 bit Ubuntu? If so, how would I do that? 

(If I should ask this in a different forum, please help me move it or I'll delete it and reask in the appropriate forum.)

Thanks!

Aaron

---

### Post by dcstar on 2010-11-20
> **aaronchall said:**
> So I just (impulsively) bought a Dell Studio 1558 with 6GB RAM and an arrandale i5-460M processor. As I'm a huge Ubuntu fanboy, I really need it to work with Ubuntu. Am I in trouble? 

Do you think I should partition and install 32 bit AND 64 bit Ubuntu? If so, how would I do that? 


Just manually set up a separate /home partition and a 10GB / partition for the 32-bit install (along with a swap partition equal to your RAM size), then install 64-bit on its own 10GB / partition (using the common /home) and you can boot both versions and see which one works best for you.

All you will lose is a little disk space and some time doing the second install.

---

### Post by aaronchall on 2010-11-20
> **dcstar said:**
> Just manually set up a separate /home partition and a 10GB / partition for the 32-bit install (along with a swap partition equal to your RAM size), then install 64-bit on its own 10GB / partition (using the common /home) and you can boot both versions and see which one works best for you.

All you will lose is a little disk space and some time doing the second install.

After some reco's on Ubuntu's IRC channel, I think I'm going to just do the 64bit install and see how that works. I'm relatively confident after reading posts regarding my model that I'm not going to have huge issues. (headphones might be one, but at least the hardware should work on this model, as opposed to the one I'm typing this on... sigh...)

But thanks for the suggestions for the multiple installs! Maybe I'll do that to try Mint, Kubuntu, and/or Debian. I'm definitely NOT going to boot natively into Windows. It can live on a virtual machine, where it can't do much harm...

---

### Post by dcstar on 2010-11-20
> **aaronchall said:**
> 
.........
But thanks for the suggestions for the multiple installs! Maybe I'll do that to try Mint, Kubuntu, and/or Debian.
.........

Do not use a common /home for different distros - the varying versions of thing like Gnome can break functionality as config files can get upgraded to new structures that are then incompatible when booting versions that depend on the older structure.

Only use a common /home for things like the same release of Ubuntu/Kubuntu/32-bit/64-bit etc.

---


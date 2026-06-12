---
title: "RAM query..."
date: 2012-01-29
forum: General Help
---

### Post by pooper on 2012-01-29
Basically about a year ago I got a motherboard bundle, including mobo, 1gb ram and 64 bit processor. 
due to installation issues I went with 32bit os. 
I've just installed another 4gb of ram, now it has 5gb in total.
I've tested both ports and both sticks of ram, all seems to be fine. 
However all the os keeps telling me I have is 3gb. I've run software which confirms both sticks of ram are recognised. 

I'm wondering, is this due to the operating system being 32bit?

---

### Post by Wayne_V on 2012-01-29
try the pae kernel:

$ sudo apt-get install linux-generic-pae

---

### Post by pooper on 2012-01-29
what does it do? and how to use it?

---

### Post by Wayne_V on 2012-01-29
[https://help.ubuntu.com/community/EnablingPAE](https://help.ubuntu.com/community/EnablingPAE)

it is the kernel that enables 32bit os to see >3G ram.    you just install it and reboot.

---

### Post by pooper on 2012-01-29
ok cool, thanks a lot. I shall reboot now!

---

### Post by Slim Odds on 2012-01-29
> **pooper said:**
> Basically about a year ago I got a motherboard bundle, including mobo, 1gb ram and 64 bit processor. 
due to installation issues I went with 32bit os. 
I've just installed another 4gb of ram, now it has 5gb in total.
I've tested both ports and both sticks of ram, all seems to be fine. 
However all the os keeps telling me I have is 3gb. I've run software which confirms both sticks of ram are recognised. 

I'm wondering, is this due to the operating system being 32bit?

Indeed it is the 32 bit OS. Any 32 bit OS only has a 4GB address space. However, some of that space is needed for hardware addressing, so the actual space that you get varies depending on the machine. Usually somewhere between 3.5 to 3.8 GB.

As was mentioned, you can install the PAE kernel which allows a larger address space at the cost of a little speed.

The only other real options is to reinstall with the 64 bit version. Personally, I'd prefer the 64 bit OS, but that does require quite a bit of additional work in this case.

---

### Post by pooper on 2012-01-29
I've just rebooted and entered the pae on the boot menu, but it's command line?

anyway I think I will switch over to 64bit as the only reason I didn't in first place was due to an incompatible driver which I no longer require..

I have all my hd in partitions so no big deal swapping the os

thanks for the help

---

### Post by Wayne_V on 2012-01-29
64 bit probably is best but to get fix the problem of no X with the pae kernel you probably just need to install the pae modules/headers packages as well.   look at 'apt-cache search pae'

---

### Post by pooper on 2012-01-29
another quick question, I have 2 partitions, one is root / , the other is /home

I'm assuming I can just write over root with a 64bit version and it will automatically use my existing /home partition?

---

### Post by Wayne_V on 2012-01-30
It *should*, yes.  But I would note which partition is which ahead of time and then you can verify during the install that it detected them properly (and correct if necessary).   

What version are  you running?  You *may* be able to just do an update to the 64-bit version as opposed to a full re-install.   If it lets you I think that would be better.

---

### Post by xyzzyman on 2012-01-30
Running with 5GB's of RAM may be slower than going with 4GB's. Are you running 2x2g+2x512MB or 2x2g+1g? I don't know your usage, but most people don't use all of their 4GB's (I don't) so if you have a multi-core CPU, dropping your RAM to single-channel slows things down. Using matching pairs to stay in dual-channel is best.

---

### Post by Slim Odds on 2012-01-30
> **xyzzyman said:**
> Running with 5GB's of RAM may be slower than going with 4GB's. Are you running 2x2g+2x512MB or 2x2g+1g? I don't know your usage, but most people don't use all of their 4GB's (I don't) so if you have a multi-core CPU, dropping your RAM to single-channel slows things down. Using matching pairs to stay in dual-channel is best.

That all depends on the motherboard.

---

### Post by pooper on 2012-01-30
i'm running ubuntu 10.04, thinking of going for a nice clean install of 64bit 10.04

---

### Post by xyzzyman on 2012-01-30
With the new LTS 12.04 coming up in a few months, maybe you might want to put 11.10 64bit on, as 12.04 is mostly stability and usability tweaks and will be less of a change for the upgrade.

If you are not going with 11.04/11.10 because you don't want to use Unity, then maybe you might want to look at xubuntu 11.10.

---


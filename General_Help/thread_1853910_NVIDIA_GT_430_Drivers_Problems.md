---
title: "NVIDIA GT 430 Drivers Problems"
date: 2011-10-03
forum: General Help
---

### Post by Gibbs on 2011-10-03
Hi,

I have a Zotac Z68-ITX-B-E mini-itx motherboard that comes with an NVIDIA GeForce GT 430 GPU and am struggling on getting the video driver to work.

Jockey doesn't display any drivers whatsoever. If I install the drivers provided on the NVIDIA website it falls over saying the module couldn't be loaded.

Any suggestions? This is for 10.04 LTS.

Cheers

---

### Post by Pafuri on 2011-10-03
Hi there

Have the same problem. I have read the posts over and over since April I think. Have tried so many things I'm not sure what I've done. Got same video card. Started with clean install of ubuntu 11.04, then 10.04, upgraded to 10.10 and still no luck. Eventually clean install ubuntu 10.04LTS. In short what I tried to no avail(and still booting in low graphics mode): 

(this is my first post, im a newby, so please forgive me for not having all the know how)

I've purged nvidia, re-installed latest nvidia current and common through synaptic, blacklisted a bunch of stuff.
Even got nvidia to say it's activated AND in use but still low graphics at reboot.
did sudo lsmod etc
tried sudo nvidia-xconfig many many times

installed nvidia through synaptic and through terminal and through tty1 or whatever
never installed nvidia though their website, too scared from reading the posts

have to go home after work to get more specific to what i have done. Have to let you know that i converted to ubuntu 2 years ago(laptop) and will NEVER go back to the other OS's! This nvidia problem started when i installed ubuntu on my hp pavillion desktop. I really hope there is someone out there that can help us, we are in the same boat...

---

### Post by Bobhuber on 2011-10-03
> **Gibbs said:**
> Hi,

I have a Zotac Z68-ITX-B-E mini-itx motherboard that comes with an NVIDIA GeForce GT 430 GPU and am struggling on getting the video driver to work.

Jockey doesn't display any drivers whatsoever. If I install the drivers provided on the NVIDIA website it falls over saying the module couldn't be loaded.

Any suggestions? This is for 10.04 LTS.

Cheers
I have the same card and found that the newest drivers supplied by x-org edgers (285.03) seem to work the best . Be aware that these drivers are the latest and sometimes experimental . No guarantee with your motherboard but worth a try and can be installed and uninstalled fairly easily. The easiest way for quick uninstall if needed is to install the PPA thru Ubuntu tweak or install ppa-purge .

---

### Post by Gibbs on 2011-10-03
> **Bobhuber said:**
> I have the same card and found that the newest drivers supplied by x-org edgers (285.03) seem to work the best . Be aware that these drivers are the latest and sometimes experimental . No guarantee with your motherboard but worth a try and can be installed and uninstalled fairly easily. The easiest way for quick uninstall if needed is to install the PPA thru Ubuntu tweak or install ppa-purge .

Thanks, will give this a shot (its a clean install with nothing on it worth saving).

**@Pafuri**
If you are in the mood for experimenting without fear of making your system unstable try this (I can't get around to it until tomorrow):
```
sudo apt-add-repository ppa:xorg-edgers/ppa
```

Worst case scenario fix would probably be a simple:
```
sudo ppa-purge xorg-edgers
```

---

### Post by Pafuri on 2011-10-03
I have no trouble experimenting will give it a try tonight. Im here to learn. I do remember that i did add some ppa and xorg to the repository a while back. Many thanks will try your advice anyway, will get back with results:)

---

### Post by pqwoerituytrueiwoq on 2011-10-03
i am using a gt 430 on my desktop and it work fine with ubuntu 10.04 (10.04 lacks vdpau out of the box (unlike 10.10), vdpau does wonders for 1080p playback)
```
sudo apt-add-repository ppa:ubuntu-x-swat/x-updates;sudo apt-get update;sudo apt-get upgrade
```
i think natty has some issue with activating the driver
make sure [FONT="Courier New"]nomodeset[/FONT] is in your kernel boot line

---


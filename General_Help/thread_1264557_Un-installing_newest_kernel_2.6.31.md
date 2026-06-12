---
title: "Un-installing newest kernel 2.6.31"
date: 2009-09-12
forum: General Help
---

### Post by DeMus on 2009-09-12
Hi all,

I just downloaded the three files necessary to install the latest kernel, version 2.6.31 from this site: [_Kernels_]("http://kernel.ubuntu.com/~kernel-ppa/mainline/").
One by one I installed them using Gdebi and this went fine. I rebooted and found out 2 of my temp sensors are not detected automatically. I show the temps in the top panel, 2 gave me ERROR. In the previous kernels they all function well.
So, I rebooted into 2.6.30 (the previous one) and it's working fine.

Problem is: how do I uninstall a kernel when I don't see it mentioned in Synaptic, neither in Add/Remove?
I tried using dpkg but the format is unknown to me. I got a message I should use the name of the package, not the file-name in came in.

When I have these 3 files:
linux-headers-2.6.31-020631_2.6.31-020631_all.deb
linux-headers-2.6.31-020631-generic_2.6.31-020631_amd64.deb
linux-image-2.6.31-020631-generic_2.6.31-020631_amd64.deb

what are the package names and what is the exact syntax to remove and purge everything belonging to this kernel version?

---

### Post by Bonster on 2009-09-12
in synaptic, look for linux-image-2 and look at the version u want to uninstall and mark for complete removal

---

### Post by DeMus on 2009-09-13
> **Bonster said:**
> in synaptic, look for linux-image-2 and look at the version u want to uninstall and mark for complete removal

That's what I thought so to, and that's what I have done so already, but as I wrote in my initial post:
Problem is: how do I uninstall a kernel when I don't see it mentioned in Synaptic.
It's not there so I can not uninstall it that way.

---

### Post by akakingess on 2009-09-13
Are you testing Karmic? I just downloaded it via update -a to get to Alpha 5 and I am curious about the same thing, although probably for different reasons.

---

### Post by DeMus on 2009-09-13
> **akakingess said:**
> Are you testing Karmic? I just downloaded it via update -a to get to Alpha 5 and I am curious about the same thing, although probably for different reasons.

No, I use Jaunty but installed the latest kernel. Unfortunately there is an error in it so I went back to the previous version. Now I can't uninstall it.

---

### Post by sgosnell on 2009-09-13
First, boot to your previous kernel using Esc as soon as the BIOS screen goes away.  Then, you should be able to open Synaptic and find the .31 kernel.  It's listed as linux-image-2.6.31-something, depending on the version you installed.  Click on it, select Mark for removal, then Apply, and it should be gone.  If you don't see it in Synaptic, something has gone horribly wrong, or else it has already been removed.

---

### Post by DeMus on 2009-09-13
> **sgosnell said:**
> First, boot to your previous kernel using Esc as soon as the BIOS screen goes away.  Then, you should be able to open Synaptic and find the .31 kernel.  It's listed as linux-image-2.6.31-something, depending on the version you installed.  Click on it, select Mark for removal, then Apply, and it should be gone.  If you don't see it in Synaptic, something has gone horribly wrong, or else it has already been removed.

It's not mentioned in Synaptic and it is not removed already since I could not do that, plus I can still boot into it. It still works, except for the one error I found with my temp. sensors.
So, one thing left: something has gone horribly wrong, as you mentioned. What it is, I don't know. I am now using 2.6.30 again and things are running fine. I set the default value in menu.lst to 2 to boot 2.6.30 automatically.
Thanks for your answer, as I said things are running fine. I just wish to know how it's possible that an installed program does not show up in synaptic.

---

### Post by renkinjutsu on 2009-09-13
use apt-get or aptitude to uninstall it

sudo aptitude remove linux-image [then start tabbing till stuff pop up] .. that usually works

also, in synaptic, don't do a quick search
if you want to find a custom installed kernel, actually click on the search button for the search dialog to pop up and type in linux-image or linux-headers

---

### Post by DeMus on 2009-09-13
> **renkinjutsu said:**
> use apt-get or aptitude to uninstall it

sudo aptitude remove linux-image [then start tabbing till stuff pop up] .. that usually works

also, in synaptic, don't do a quick search
if you want to find a custom installed kernel, actually click on the search button for the search dialog to pop up and type in linux-image or linux-headers

Thanks, that did it. I used the quick-search because I always do that. I can find the other kernel versions with it, but nor the latest one. Now it's gone. Thanks a lot.

---

### Post by sgosnell on 2009-09-13
I haven't seen that happen.  Every kernel I've ever installed has been in Synaptic, but maybe you're doing the install differently.  I get mine from [kernel.ubuntu.com](http://kernel.ubuntu.com/~kernel-ppa/mainline/) as a .deb file, and install it with gdebi.  I don't do any manual file editing or anything else.

---

### Post by DeMus on 2009-09-15
> **sgosnell said:**
> I haven't seen that happen.  Every kernel I've ever installed has been in Synaptic, but maybe you're doing the install differently.  I get mine from [kernel.ubuntu.com](http://kernel.ubuntu.com/~kernel-ppa/mainline/) as a .deb file, and install it with gdebi.  I don't do any manual file editing or anything else.

I also installed .deb files from kernels.ubuntu.com using Gdebi. I just didn't see it appearing in Synaptic afterwards, until I used search instead of quick-search. Then I could uninstall it all again.

---

### Post by sgosnell on 2009-09-16
Mine show up in Synaptic using either search.  I don't know why yours don't.

---


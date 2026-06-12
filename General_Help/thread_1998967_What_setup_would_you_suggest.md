---
title: "What setup would you suggest?"
date: 2012-06-07
forum: General Help
---

### Post by dano2 on 2012-06-07
I'm setting up my notebook from scratch, and I'm hoping some more experienced folks can give their recommendations in terms of how much HD space to allot, VM vs Dual Boot, etc. I have an ASUS G73S w/ 8G Ram and 500G Hardrive (2 x 250G). 

My primary uses will be:

-- First and foremost - Web/Android development (ubuntu ). Most TIME will be spent here.
-- Image & movie editing with Adobe Photoshop and Premier Pro (windows 7). Most HD space will be required here.
-- Routine Internet Stuff

So, to test IE and for various editing, I need to be able to quickly bounce between Windows & Ubuntu. So VirtualBox (instead of dual booting) seemed to be a logical idea, but I'm reluctant because when I used it a couple years ago there was considerable latency. Not good for Image/Movie editing. But dual booting makes Web Development a nightmare, having to reboot all the time just to test IE.

I'm hoping I'm just not up with the latest and greatest of what's out there, and there's an obvious solution someone can suggest. Thanks in advance :tongue:

---

### Post by idoitprone on 2012-06-07
> **dano2 said:**
> I'm setting up my notebook from scratch, and I'm hoping some more experienced folks can give their recommendations in terms of how much HD space to allot, VM vs Dual Boot, etc. I have an ASUS G73S w/ 8G Ram and 500G Hardrive (2 x 250G). 

My primary uses will be:

-- First and foremost - Web/Android development (ubuntu ). Most TIME will be spent here.
-- Image & movie editing with Adobe Photoshop and Premier Pro (windows 7). Most HD space will be required here.
-- Routine Internet Stuff

So, to test IE and for various editing, I need to be able to quickly bounce between Windows & Ubuntu. So VirtualBox (instead of dual booting) seemed to be a logical idea, but I'm reluctant because when I used it a couple years ago there was considerable latency. Not good for Image/Movie editing. But dual booting makes Web Development a nightmare, having to reboot all the time just to test IE.

I'm hoping I'm just not up with the latest and greatest of what's out there, and there's an obvious solution someone can suggest. Thanks in advance :tongue:

15GB / for root up to 20GB i guess
8GB swap
Allocate the rest for home

You can put all linux partitions in one extended partition

You decided how big you wnat windows and linux


KVM benchmarks is not that bad
Virtual Box is ok too
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_1110_xenkvm&num=4](http://www.phoronix.com/scan.php?page=article&item=ubuntu_1110_xenkvm&num=4)
VIrtualization software gets better as hardware support improves


I will have to say there is a problem with the movie editing and image editing. Virtualization overhead is pretty high

wine is your best bet to run it under linux
[http://appdb.winehq.org/appview.php?appId=17](http://appdb.winehq.org/appview.php?appId=17)
Priemere Pro status is garbage, dont even bother installing in linux 
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=128](http://appdb.winehq.org/objectManager.php?sClass=application&iId=128)

If you edit for your own livelihood, i would not bother with wine other than photoshop, since raster images should not screw up as often

You should boot into windows when you work on video and images

---

### Post by 11jmb on 2012-06-07
I'm not as familiar with Virtualbox, but VMware allows 3D acceleration, which speeds up graphics-intensive processes significantly. Perhaps Virtualbox has the same features?

Virtualization will always be slower than a native OS, but for testing on IE, you should be fine inside a VM. 

A windows VM may not be sufficient for your photo/video editing, so perhaps a windows host with an Ubuntu VM may work better for you.

---

### Post by holycow131415 on 2012-06-07
Yeah it sounds like you need it the other way around. W7 as host, ubuntu as guest unless you want to learn gimp for photo editing and use open shot for video editing.

---


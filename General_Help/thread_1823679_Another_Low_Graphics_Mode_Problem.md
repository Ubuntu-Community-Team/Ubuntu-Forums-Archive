---
title: "Another Low Graphics Mode Problem"
date: 2011-08-12
forum: General Help
---

### Post by holadebob on 2011-08-12
This problem is getting me pretty frustrated...

For about two months or so my system has been interrupted with a "You are running in low graphics mode" and I can't get it fixed. It interrupts everything I'm doing, destroying every job in progress.

I have googled and googled and haven't found any solutions.

I have Intel 82945G/GZ integral video circuit, Celeron 2.8Gb processor, 3.347 gb ram. 

Never had this problem three months ago, have been running 10.04 since 10/10. I'm using kernel 2.6.32-21 because I thought the newer kernels were the problem.

Please help!!!

---

### Post by dino99 on 2011-08-12
as actual kernel directly deal with X, xorg.conf is no more needed by default. Need to configure it only with special display like tv/non-lcd or multiple displays

sudo rm /etc/X11/xorg.conf
(or rename it if you care about it)

then open synaptic to remove/purge then reinstall xserver-xorg-video-intel

shutdown & make a cold boot

---

### Post by holadebob on 2011-08-12
Thanks Dino, I did what you said and hoping that everything ends out good.

---

### Post by holadebob on 2011-08-12
That appears to have solved my problem - it's been humming along without error for a few hours.

Thank you for the rescue!

---

### Post by holadebob on 2011-08-17
Just had another low graphics mode warning. The file xorg.conf does not exists. I will go ahead and purge/reinstall  xserver-xorg-video-intel.

The strange thing is that the first time I followed your directions, there was no xorg.conf file there. There was a xorg.conf failsafe file, however.

Since the problem came back, is there another solution you folks can come up with?

Thank you

---


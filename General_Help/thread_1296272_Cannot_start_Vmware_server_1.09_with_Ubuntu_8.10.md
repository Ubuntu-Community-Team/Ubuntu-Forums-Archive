---
title: "Cannot start Vmware server 1.09 with Ubuntu 8.10"
date: 2009-10-20
forum: General Help
---

### Post by SunnyUbu on 2009-10-20
Hi, I am in need of some advice with my Ubuntu 8.10 & vmware server 1.09 setup.
I had some initial issues with installation but after reading around and googling I managed to complete the install.

Up until this afternoon I had vmware server working with several virtual machines.

Now when I click the vmware server icon, it flashes, appearing to start and then goes blank. I tried to run vmware-install.pl and this had no effect.


I have used vmware-update-2.6.27-5.5.7-2 in my setup.

So what changed? I was playing around wih my sound card earlier today but not sure if that had any effect?

I am lost and would appreciate some help in troubleshooting this/ fixing this.

Thanks in advance!


Sunny

---

### Post by i.r.id10t on 2009-10-20
Open a terminal and start it - it will give you more error info.  My guess is a new kernel is causing issues for your modules and you'll need to rebuild them.

---


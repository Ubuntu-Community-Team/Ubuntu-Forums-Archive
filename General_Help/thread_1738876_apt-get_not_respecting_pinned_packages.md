---
title: "apt-get not respecting pinned packages"
date: 2011-04-25
forum: General Help
---

### Post by imbjr on 2011-04-25
I have the edgers ppa installed and I pinned:

 xserver-xorg-video-ati
 xserver-xorg-video-radeon

When I run apt-get upgrade, I'm told that those two can be upgraded, which I'd rather not do - hence the pinning. 

Going into synaptic shows that there are no updated versions available for these two packages - until I specifically check versions available!

So is there way to have apt-get stick with the pins set in synaptic?

---

### Post by lithopsian on 2011-04-25
Post the results of ```
apt-cache policy xserver-xorg-video-ati xserver-xorg-video-radeon
```It might also help to show the apt config you have right now.

---

### Post by imbjr on 2011-04-25
> **lithopsian said:**
> Post the results of ```
apt-cache policy xserver-xorg-video-ati xserver-xorg-video-radeon
```It might also help to show the apt config you have right now.

I get:

> 
xserver-xorg-video-ati:
  Installed: 1:6.14.99+git20110214.a9a59717-0ubuntu0sarvatt2~maverick
  Candidate: 1:6.14.99+git20110307.6319a33c-0ubuntu0sarvatt~maverick
  Version table:
     1:6.14.99+git20110307.6319a33c-0ubuntu0sarvatt~maverick 0
        500 [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/) maverick/main i386 Packages
 *** 1:6.14.99+git20110214.a9a59717-0ubuntu0sarvatt2~maverick 0
        100 /var/lib/dpkg/status
     1:6.13.2+git20110107.0e432dff-0ubuntu0tormod 0
        500 [http://ppa.launchpad.net/xorg-edgers/radeon/ubuntu/](http://ppa.launchpad.net/xorg-edgers/radeon/ubuntu/) maverick/main i386 Packages
     1:6.13.1-1ubuntu5 0
        500 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick/main i386 Packages
xserver-xorg-video-radeon:
  Installed: 1:6.14.99+git20110214.a9a59717-0ubuntu0sarvatt2~maverick
  Candidate: 1:6.14.99+git20110307.6319a33c-0ubuntu0sarvatt~maverick
  Version table:
     1:6.14.99+git20110307.6319a33c-0ubuntu0sarvatt~maverick 0
        500 [http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/](http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu/) maverick/main i386 Packages
 *** 1:6.14.99+git20110214.a9a59717-0ubuntu0sarvatt2~maverick 0
        100 /var/lib/dpkg/status
     1:6.13.2+git20110107.0e432dff-0ubuntu0tormod 0
        500 [http://ppa.launchpad.net/xorg-edgers/radeon/ubuntu/](http://ppa.launchpad.net/xorg-edgers/radeon/ubuntu/) maverick/main i386 Packages
     1:6.13.1-1ubuntu5 0
        500 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) maverick/main i386 Packages


which does agree with my discovery in synaptic that there are indeed upgradable versions available. Synaptic does not advertise this though, you have to manually check the versions, and as I say, it looked like apt-get didn't care about the pinned status of what was installed.

---

### Post by dino99 on 2011-04-25
remove/purge then reinstall those packages

---

### Post by imbjr on 2011-04-25
> **dino99 said:**
> remove/purge then reinstall those packages

I'm not sure I follow your reasoning.

I want to stay at the versions I have installed, but if I am trying to use apt-get it looks like it wants to override what I have pinned and install the latest versions.

I'm not sure what purge/re-install will do to convince apt-get to not do that.

---

### Post by imbjr on 2011-04-27
Well I went ahead with the upgrade anyway and it all seemed good, but then Google Earth performance seemed to take a hit, so I reverted the drivers back and pinned them.

But still, apt-get does not care about this pinning. It looks like it will just go ahead and restore the already downloaded drivers.

Fortunately, I mainly use synaptic on my main machine, but what if this were the server? It would be a pain to have to avoid accidentally upgrading something you've pinned there.

---

### Post by RHTopics on 2011-04-27
As you have discovered, apt-get does not recognize when a package is locked by Synaptic.

Instead, you will need to use dpkg to place the package on hold.

Here is a link to help documentation for more information:

[https://help.ubuntu.com/community/PinningHowto](https://help.ubuntu.com/community/PinningHowto)

---

### Post by imbjr on 2011-04-27
> **RHTopics said:**
> As you have discovered, apt-get does not recognize when a package is locked by Synaptic.

Instead, you will need to use dpkg to place the package on hold.

Here is a link to help documentation for more information:

[https://help.ubuntu.com/community/PinningHowto](https://help.ubuntu.com/community/PinningHowto)

Thanks for this.

---


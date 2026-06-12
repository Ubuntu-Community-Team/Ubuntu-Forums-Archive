---
title: "HELP: ATI proprietary driver &amp; Maverick"
date: 2010-10-14
forum: General Help
---

### Post by 68pontiac on 2010-10-14
Alright, I'm in need of some help. I just upgraded from Lucid to Maverick and I absolutely cannot get the proprietary fglrx driver to install. I've downloaded the binaries from ATI and they fail to install with a message that says:```
Error: ./default_policy.sh does not support version
default:v2:i686:lib::none:2.6.35-22-generic:; make sure that the version is being
correctly set by --iscurrentdistro

Removing temporary directory: fglrx-install.Dtv3Sn
```
I tried installing the drivers from the System>Administration>Additional Drivers and it fails with```
SystemError: installArchives() failed
```

Based on what little I could find I guess the newest version of Xorg broke the ATI drivers. Is this true and is there absolutely no way to use the proprietary drivers?

I'm a World of Warcraft nerd and the fglrx drivers are the only ones that work for me

---

### Post by alphacrucis2 on 2010-10-15
> **68pontiac said:**
> Alright, I'm in need of some help. I just upgraded from Lucid to Maverick and I absolutely cannot get the proprietary fglrx driver to install. I've downloaded the binaries from ATI and they fail to install with a message that says:```
Error: ./default_policy.sh does not support version
default:v2:i686:lib::none:2.6.35-22-generic:; make sure that the version is being
correctly set by --iscurrentdistro

Removing temporary directory: fglrx-install.Dtv3Sn
```
I tried installing the drivers from the System>Administration>Additional Drivers and it fails with```
SystemError: installArchives() failed
```

Based on what little I could find I guess the newest version of Xorg broke the ATI drivers. Is this true and is there absolutely no way to use the proprietary drivers?

I'm a World of Warcraft nerd and the fglrx drivers are the only ones that work for me

Catalyst 10.9 from the ATI website will definitely not work with Maverick. The one in the Maverick repo is a pre release of Catalyst 10.10 which ATI haven't made generally available yet. That is the version you want. Just install it via the System menu in Maverick but you need to get rid of the old fglrx first. Try:


```
sudo sh /usr/share/ati/fglrx-uninstall.sh
```

---

### Post by 68pontiac on 2010-10-15
> **alphacrucis2 said:**
> Catalyst 10.9 from the ATI website will definitely not work with Maverick. The one in the Maverick repo is a pre release of Catalyst 10.10 which ATI haven't made generally available yet. That is the version you want. Just install it via the System menu in Maverick but you need to get rid of the old fglrx first. Try:


```
sudo sh /usr/share/ati/fglrx-uninstall.sh
```

Thanks for the response. I've tried that, it uninstalls perfectly as it always has before. When installing the fglrx package from Synaptic I'm given this wonderful error```
E: /var/cache/apt/archives/fglrx_2%3a8.780-0ubuntu2_i386.deb: subprocess new pre-installation script returned error exit status 1
```

There is also a lot of information in the terminal window that Synaptic provides but I can't seem to copy/paste it here so I made some screenshots. I hope someone can help me out here. Thanks again

[IMG]http://lh5.ggpht.com/_QgNcd_3tPVY/TLh9i1DRS9I/AAAAAAAAAIs/aVFb3YptW0U/Screenshot-1.png[/IMG]
[IMG]http://lh6.ggpht.com/_QgNcd_3tPVY/TLh9jKLh-aI/AAAAAAAAAIw/ZY_oRh7NRHE/Screenshot-2.png[/IMG]
[IMG]http://lh5.ggpht.com/_QgNcd_3tPVY/TLh9japD5DI/AAAAAAAAAI0/dX1vg0W9_Rw/Screenshot-3.png[/IMG]

---

### Post by 68pontiac on 2010-10-15
So my problem has been partially solved. With some additional Googling I found a "beta" 10.10 binary driver that installed and works. My only complaint now is that in the bottom right corner of my screen I have an AMD logo and "TESTING USE ONLY" stuck there until I can get my hands on the real 10.10 drivers.

Can anybody figure out why the version in the Ubuntu Repos won't install for me?

---


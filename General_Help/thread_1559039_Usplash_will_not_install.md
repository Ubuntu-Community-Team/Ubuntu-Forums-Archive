---
title: "Usplash will not install"
date: 2010-08-23
forum: General Help
---

### Post by frekimedia on 2010-08-23
I hope this is just a really dumb/easy fix. I installed startup-manager to change the appearance of my boot screen, but it doesn't have an "Appearance" tab! I checked and I don't think I have usplash installed, when I apt-get usplash I get this error:

```
apt-get install usplash
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  usplash: Depends: initramfs-tools (>= 0.92bubuntu55) but it is not going to be installed
           Depends: upstart (>= 0.6.3-4) but it is not going to be installed
           Recommends: usplash-theme-ubuntu but it is not going to be installed or
                       usplash-theme
E: Broken packages

```

I'm running Lucid Lynx (10.04) 64-bit.

Can anyone help? I'd really like to get startup-manager working! Thanks all!

---

### Post by frekimedia on 2010-08-23
Forgot to mention, initramfs-tools and upstart are both installed to their most current version. Thanks!

---


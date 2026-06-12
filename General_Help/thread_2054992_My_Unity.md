---
title: "My Unity"
date: 2012-09-08
forum: General Help
---

### Post by rickm1945 on 2012-09-08
I installed My Unity and my laptop is running Unity 2D. This is because of Sandybridge Video drivers for Intel intergrated graphics.. Will Ubuntu 12.10 have these updated drives? This HP Laptop is less than 6 months old. How can I remove My Unity? I am getting error messages about internal system error. I send them in but I think maybe I should not keep My Unity.

---

### Post by Epodx64 on 2012-09-08
You can get better drivers from here
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)
add the ppa then run
sudo apt-get update
sudo apt-get upgrade

---

### Post by Frogs Hair on 2012-09-08
2D will no longer be installed by default on 12.10 [http://www.webupd8.org/2012/08/unity-2d-no-longer-installed-by-default.html](http://www.webupd8.org/2012/08/unity-2d-no-longer-installed-by-default.html)  

You can remove MyUnity from the software center by selecting remove. If you are using 2D only this tool may make more sense, though it has less features. [http://marianochavero.wordpress.com/2012/03/14/small-desktop-configuration-tool-for-ubuntu-unity-2d-12-](http://marianochavero.wordpress.com/2012/03/14/small-desktop-configuration-tool-for-ubuntu-unity-2d-12-)

---

### Post by rickm1945 on 2012-09-08
> **Frogs Hair said:**
> 2D will no longer be installed by default on 12.10 [http://www.webupd8.org/2012/08/unity-2d-no-longer-installed-by-default.html](http://www.webupd8.org/2012/08/unity-2d-no-longer-installed-by-default.html)  

You can remove MyUnity from the software center by selecting remove. If you are using 2D only this tool may make more sense, though it has less features. [http://marianochavero.wordpress.com/2012/03/14/small-desktop-configuration-tool-for-ubuntu-unity-2d-12-](http://marianochavero.wordpress.com/2012/03/14/small-desktop-configuration-tool-for-ubuntu-unity-2d-12-)
The eliminating 2D sounds good. I just hope they have the updated Sandybridge drivers for Intel graphics. That my problem on my laptop which is only 5 months old. Runs fine in Windows 7 but not Ubuntu 12.04. Hoping for the best.

---

### Post by Epodx64 on 2012-09-10
> **rickm1945 said:**
> The eliminating 2D sounds good. I just hope they have the updated Sandybridge drivers for Intel graphics. That my problem on my laptop which is only 5 months old. Runs fine in Windows 7 but not Ubuntu 12.04. Hoping for the best.

Have you tried downloading the i965 Drivers? add these packages
sudo apt-get install i965-va-driver

then open up ubuntu software center and search for va and download all the VA API files it seems to work pretty good this wont replace the the i915 driver but runs with it

---

### Post by rickm1945 on 2012-09-10
> **Epodx64 said:**
> Have you tried downloading the i965 Drivers? add these packages
sudo apt-get install i965-va-driver

then open up ubuntu software center and search for va and download all the VA API files it seems to work pretty good this wont replace the the i915 driver but runs with it
Would I need to remove "nomodeset" before installing the i965 drivers? I'm surmising that I would but want to verify.

---

### Post by Epodx64 on 2012-09-10
no what you need to download is the intel-xorg-xserver (look up the name) and that will add the i915 driver that should let you take nomodeset off then add the i965 drivers

---

### Post by rickm1945 on 2012-09-12
> **Epodx64 said:**
> no what you need to download is the intel-xorg-xserver (look up the name) and that will add the i915 driver that should let you take nomodeset off then add the i965 drivers
I saw the xorg packages on Launchpad, but I don't know which one to download and how do I install them. Your idea sounds like the most logical I have gotten about this video problem. Please excuse my ignorance, but I'm new to Linux, only 5 months as a dedicated user. If I can get my video card to display properly it would really make my Ubuntu experience a real pleasure.

Here is the site that I was at  [https://launchpad.net/ubuntu/+source/xserver-xorg-video-intel/2:2.17.0-1ubuntu4.1](https://launchpad.net/ubuntu/+source/xserver-xorg-video-intel/2:2.17.0-1ubuntu4.1)

If you have patience to bear with me I will try this.
[]("https://launchpad.net/ubuntu/+source/xserver-xorg-video-intel/2:2.17.0-1ubuntu4.1")

---

### Post by rickm1945 on 2012-09-12
I downloaded  the deb file ```
xserver-xorg-video-intel_2.20.5+git20120830.deaa1cac-0ubuntu0ricotz~precise_amd64(1).deb
``` I click it to install and got this error. See screen shot.

---


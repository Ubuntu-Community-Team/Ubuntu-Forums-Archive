---
title: "Help with Fn key with wireless"
date: 2009-08-02
forum: General Help
---

### Post by hinesdeal102 on 2009-08-02
Hi everyone, I have made/used plenty of Ubuntu boxes in the past but now I have a notebook (Asus K50ij) and I find myself not being able to deal with the......hassles of windows anymore.  Vista 64 is buggy on this notebook so I popped in my Ubuntu 9.04 live CD and it ran great, it was faster off the live cd then windows running from the hard drive believe it or not.  The one thing that didn't work which is very much necessary for me is that the wireless network card would not activate.  There is an l.e.d. that tells me if the wireless is turned on and it does not light up in Ubuntu, however in windows it works and and functions because of the software that allows me to switch it on and off via the Fn+F2 key combination.  I really do think that the driver is there in Ubuntu but I think it's simply deactivated and the Fn key does not work for that.  I should add that the Fn key combination's work with the other controls (brightness, volume) but not for the wireless.  The wireless chip is an Atheros AR9285 and I only have wireless access via the neighbors so I can't really use synaptic to download anything from within Ubuntu.  Any help would be greatly appreciated, I really need a stable OS; Windows just seems to crash allot on this notebook, thanks to all the junk that is deeply integrated....sorry, rambling.

---

### Post by shane8002 on 2009-08-02
The ath5k driver should work that wireless card. Have you enabled it under hardware drivers??  Also to get the wireless led's working you might half to edit the config file for it to work. Jaunty is pretty good about wireless drivers and your card should show up under administration-hardware drivers. If it still dosent work there should be an option to revert to madwifi drivers. Between the two, one of them should work.

---

### Post by hinesdeal102 on 2009-08-02
The card does not appear under the restricted drivers.  If I issue the command ifconfig, it just shows up as there being no wireless device.  If I run lspci then the card shows up as the Atheros AR9285.  This is what leads me to believe that the driver is functional but the card is simply turned off.  Where should I go from here?

---

### Post by shane8002 on 2009-08-03
Under terminal run sudo modprobe lspci.

then try sudo modprobe ath5k.

---

### Post by hinesdeal102 on 2009-08-03
sudo modprobe lspci returned a fatal error stating that the module can't be found. (something like that)

sudo modprobe ath5k did nothing, it gave me no output whatsoever.  Any other idea?  I do appreciate the help.  Try to throw as many ideas into one post as possible because as of right now I'm switching between Windows and a live Cd to try these things.

---

### Post by shane8002 on 2009-08-03
Okay your gonna half to use ndiswrapper to get the wireless working then when you update ubuntu 9.04 it should give yoiu an option for a new wireless driver. So make sure you update ubuntu under update manager after you do this  because ndiswrapper is a last resort driver. Go here and get your driver [http://www.atheros.cz/download.php?atheros=AR9285&system=2](http://www.atheros.cz/download.php?atheros=AR9285&system=2), then get ndiswrapper here 



[http://mirrors.kernel.org/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-common_1.53-2ubuntu1_all.deb](http://mirrors.kernel.org/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-common_1.53-2ubuntu1_all.deb)

[http://packages.ubuntu.com/jaunty/misc/ndiswrapper-utils-1.9](http://packages.ubuntu.com/jaunty/misc/ndiswrapper-utils-1.9)

[http://packages.ubuntu.com/jaunty/net/ndisgtk](http://packages.ubuntu.com/jaunty/net/ndisgtk)


You half to install them in that order so all the dependencies are satisfied. Download your driver then ndiswrapper from windows put them on a usb drive then boot up ubuntu and install ndiswrapper from the usb drive and after that installs look in the driver file for .inf then let ndiswrapper do its thing and it should work. You might half to restart im not sure but it should work, then after you update ubuntu use the driver that shows up under hardware drivers.

---

### Post by hinesdeal102 on 2009-08-07
Hi shane8002 I have been gone for a few days so I haven't got to respond.  I was able to use my friends wired connection and then I installed the jaunty backports package and that fixed the driver problem.  Thanks for all your help.

---


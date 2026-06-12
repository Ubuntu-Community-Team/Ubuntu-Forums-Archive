---
title: "Ubuntu 10.10 &amp; ati drivers"
date: 2010-10-28
forum: General Help
---

### Post by Ecip on 2010-10-28
Hello,
I'm trying to install ATI's latest driver version 10.10 on Ubuntu 10.10. I'm using the 64 bit version of Ubuntu.
In the pdf installation instructions from AMD it says the following:

The following packages must be installed in order for the ATI Catalyst&#8482; Linux driver to
install and work properly:
&#56256;&#56442; XFree86-Mesa-libGL
&#56256;&#56442; libstdc++
&#56256;&#56442; libgcc
&#56256;&#56442; XFree86-libs
&#56256;&#56442; fontconfig
&#56256;&#56442; freetype
&#56256;&#56442; zlib
&#56256;&#56442; gcc

I am finding it impossible to find these files (a few are already installed on a fresh install of Ubuntu). Would it not be possible for these to be supplied by Ubuntu or AMD?
Surely I'm not the only one looking to install these AMD ati drivers.

After an unsuccessful attempt in installing the drivers, I decided to start fresh and uninstalled the driver as per the installation instructions.. now ubuntu wont boot at all.

Anyone have a link of where to get the above files?

This is kind of a huge bump in the road for me.. i've successfully installed ubuntu x86 on my old Toshiba a100 laptop and its working marvelously.
On this highend computer I cant even get the GUI fancyies to work...

*on an additional note, i did find XFree86-Mesa-libGL in rpm format... tried to use alien to convert to deb, however it fails everytime with some kind of NOKEY error.

---

### Post by xircon on 2010-10-28
Try:

Open synaptic (alt-f2 gksu synaptic) and search for:

libgl1-mesa-glx
libglu1-mesa-
zlib1g
libfreetype6
fontconfig is there
sudo apt-get build-essential should get most of the rest

I got the drivers installed, but they are cr*p, compiz would not run so I dropped back to 10.04

---

### Post by Ecip on 2010-10-28
hello,
from what you mentioned above, all of those things seem to be installed and present.
"sudo apt-get build-essential" does not seem to work.

perhaps its just the 64 bit version of ubuntu having problems with the ati driver?
or perhaps the Radeon HD5700 isnt supported quite well?


The first time i installed the driver this morning when it all went bad, the catalyst control center was installed as i had 4 entries total under system>preferences (for some reason, CCC and CCC Admin each had a duplicate). However after clicking on any one of the 4 did nothing.. CCC would refuse to run as well as firefox scrolled very choppy, moving windows very choppy, and under appeareance>visual effects None is selected. when Normal or Extra is selected, error message informs that this is unavailable (seems ubuntu is looking for a driver..cant find one..error message).

I want to restore my computer the way it was, restore the boot loader from windows, remove the partition ubuntu added, and then try again from scratch with a fresh install.

Any other tips or info, greately appreciated. Been trying to learn a lot about linux in the past 2 days.
I will also try with the open source ati drivers available from 'Additional Drivers'. Once the open source drivers are installed and I decide to once again try and install the ATI drivers, do I need to remove the open source drivers first somehow?

---

### Post by RJ12 on 2010-10-28
Try running

```
sudo apt-get install build-essential
```


The code you used forgot the install part.

---

### Post by Ecip on 2010-10-28
ah ok, right.
I will try it again within a couple days. will be busy shortly, so this threat might suddenly spring back to life lol.
i definitely need to make some sort of knowledge database for myself for the future. :-\"

---

### Post by Ecip on 2010-10-28
> [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

When I read these instructions, point 3 under 'Introduction', correct me if I'm wrong, tells me that I have two choices when it comes to installing the proprietary ATI driver;
1) Download it from AMD or,
2) install them from the Ubuntu repositories (the fglrx drivers available via 'Additional Drivers')

So, in a way it sounds like to me that the drivers from Ubuntu are the same as can be downloaded from AMD directly..
If so, is that article still valid with Ubuntu 10.10?
And, more curiously, what's the performance difference, if any, between the two drivers? Seemss kinda important for playing games and such.
If the drivers from ubuntu repositories make use of all the capabilities of the graphics card then i'll be quite happy using those.

---

### Post by xircon on 2010-10-29
> **RJ12 said:**
> Try running

```
sudo apt-get install build-essential
```


The code you used forgot the install part.

Sorry :redface:

---

### Post by zerek on 2010-11-03
install:
```
sudo apt-get install build-essential
```
other packages should already be there.


Enabling POSIX Share Memory to load ATI drivers,
```
sudo gedit /etc/fstab
```
add:
#
tmpfs /dev/shm tmpfs defaults 0 0
```
sudo mount /dev/shm
sudo mount | grep "shm"
```

[I]If the mount was successful, then the following output (or similar) should appear:
tmpfs on /dev/shm type tmpfs (rw)[/I]



[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_cat109-inst.pdf](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_cat109-inst.pdf)
for uninstalling old drivers/installing new. 
```
sudo amdcccle
```
to open Catalyst Control Center


Hope that helps.

---


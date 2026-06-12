---
title: "help me get utilities and the dependencies?"
date: 2006-05-12
forum: General Help
---

### Post by BKK on 2006-05-12
Hi I am having a great difficulty getting my zyxel 630 11 usb modem working.
I dont want to get an ethernet modem because I think that is the easy way out and I wont learn anything. I have been trying to get it working for over a week. I have only started using linux recently.

I had hoary but gave up. Now I am trying again with breezy!

The instructions I have require me to rebuild a kernel to enable some options. I have been able to get some of the packages/utilities to compile modify etc.

I require all of the following ( so the instructions say )

sudo apt-get install build-essential bin86 kernel-package

sudo apt-get install libqt3-headers libqt3-mt-dev

I know i can get the basic build- essential, but nothing after that!

I have had little success tracking down the packages and ALL of the dependencies.  I am only able to access the internet when I boot into XP. 

I am trying to install amedyn and use rp-pppoe. I have got the entire process to work....almost.

When I ran amstart.sh it goes through to the very last step and tells me it can not load a file ( forget the name) but I KNOW its there where it should be.

I think the problem is due to the fact that when i was screwing around configuring the kernel I was getting errors and I was also unable to complete some commands due to the fact that I dont have the packages!

I have downloaded and "add-on" iso from the forums here, it didnt have what I need.

I am looking for a similar type of download with the above packages and dependencies I can get through XP!

THanks

---

### Post by kabus on 2006-05-12
Try [http://packages.ubuntu.com/](http://packages.ubuntu.com/).

---

### Post by BKK on 2006-05-12
Thanks I will look there! 

I was looking at the debian packages site!! ARGH

How about the dependencies are they all included?

Thanks

the dependency list for libqt3-mv-dev is a nightmare! dependencies of dependencies'!!
is there any other way?

---

### Post by kabus on 2006-05-12
[QUOTE=BKK]
How about the dependencies are they all included?
[/QUOTE]

If a package has any dependencies there will be links to them, you'll have to download them separately, though.

---

### Post by BKK on 2006-05-12
WOW!! 
THere are DOZENS of dependencies for some of those!! Its gonna take me a year to configure all of them! 

Shit I may just get that ethernet modem and be done with it?
Once I get online with that maybe I'll try to get the USB modem working for a learning experience, I just havent got the patience to download each dependency package and its dependencies'!!


Thanks for pointing me to the ubuntu packages tho!

cheers!

---


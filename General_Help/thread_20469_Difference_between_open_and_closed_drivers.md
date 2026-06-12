---
title: "Difference between open and closed drivers"
date: 2005-03-16
forum: General Help
---

### Post by BaffledMollusc on 2005-03-16
I'm a bit confused with regard to the 3D driver situation. I have an ATI card (X800Pro), and so installed the fglrx drivers using apt-get. This worked fine and boosted my fps by about a factor of 30. 

Now, here's my first question. Are these fglrx drivers the best possible, or are the binary drivers from ATI's site better? I initially thought they were the same, but then realised that Ubuntu does not include non-open source drivers in their standard repository, so maybe the fglrx drivers were an open-source approximation to ATI's proprietory drivers.

Second, if ATI's binary drivers are faster, *how* much faster are they? Enough to be worth the aggravation of trying to install them?

---

### Post by Scottles on 2005-03-17
The FGLRX drivers are ATi's proprietary drivers. Ubuntu ships with a version of these drivers as part of the restricted modules (..IIRC.. could be wrong), although its usually not the latest version of these (due to the feature freeze in development of Ubuntu).. To get the latest ones you need to the download the binaries from ATi's site and then perform various voodoo rituals and sacrificial ceremonies to get them working ;) 

Various people have written guides for getting them working in Ubuntu (notably myself and a guy named Bobmitch). So just do a search of the forums for instructions to install the latest FGLRX drivers :)

The DRI Project has open source drivers for older ATi cards.. but sadly ATi has not released any specifications to them for the Radeon 9700 and later.. so the only option for hardware accelerated 3d is the FGLRX drivers...

As for speed.. uh.. well.. older games based on the Quake3 engine run fine.. but newer games like UT2004 and Doom3 have performance issues... so dont expect to play any recent games at blazing speed on your card.. having said that ATi's drivers are slowly improving... probably similiar in speed to the rate at which tectonic plates move.. but hey.. some improvements better than nothing ;)

---

### Post by BaffledMollusc on 2005-03-17
[QUOTE=Scottles]The FGLRX drivers are ATi's proprietary drivers. Ubuntu ships with a version of these drivers as part of the restricted modules (..IIRC.. could be wrong), although its usually not the latest version of these (due to the feature freeze in development of Ubuntu).. To get the latest ones you need to the download the binaries from ATi's site and then perform various voodoo rituals and sacrificial ceremonies to get them working ;) 
[/QUOTE]

Yep, I looked at the instructions for installing the ATI drivers and trembled in terror. Since I don't need blazing speed or latest bugfixes I'm happy to stay with the synaptic packaged version. Besides, I'm right out of sacrificial chickens  :wink: 

Thanks for clearing that up!

---


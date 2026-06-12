---
title: "NnVidia GeForce 6200 A-LE How good is this video card"
date: 2010-12-16
forum: General Help
---

### Post by daldude on 2010-12-16
**NnVidia GeForce 6200 A-LE How good is this video card** 			
 			 			 		   		 		 		I was given a  NVidia GeForce 6200 A-LE card and when I was trying to fix a Windows XP  video problem in my Sisters PC I installed the NVidia GeForce 6200  A-LEand then installed Ubuntu 10.10 and discovered that this card has  proprietary drivers for it that I assume support hardware acceleration  so I installed the one that said "Recommended" next to the driver and  after it finished installing and I rebooted I tested the drivers by  viewing a Youtube Video full screen and it ran much smoother then  without the proprietary drivers but still had some jumpy playback. Are  these drivers stable and working at peak performance or are they still  in devolpoment and maybe buggy and / or not preforming as well as if the  card was running on a Windows XP system?

Her system is a AMD Athlon XP2100 running at 1.7 GHz with 512 MB of RAM  could it be that her system is not powerfull enough to provide optimum  performance?

  My system is running Ubuntu 10.04lts on a Pentium 4 with hyper  threading CPU running at 3.00 GHz and 1gb of RAM, ATI Radeon RV250 If  [Radeon 9000] (rev 01) that has no  proprietary drivers that support  hardware acceleration (as far as I know) will I get better performance  if I install the NVidia GeForce 6200 A-LE  video card then what I get  with my ATI card?
Am I correct in assuming that if I do wish to install the NVidia GeForce  6200 A-LE video card  I will have to reinstall Ubuntu to avoid video  driver conflicts or to insure it installs the drivers for the NVidia  GeForce 6200 A-LE?

Thanks

---

### Post by Vaphell on 2010-12-17
imo you don't have to reinstall - put the card in, at boot time it will get autodetected, probably you'll get 800x600 resolution which you will use to install closed source drivers, restart, if everything is ok you get nice res and are good to go.
By default there is no hardware acceleration for video so cpu is taxed - that's why your sis' computer is not good enough to play very inefficient flash (try to download .flv flash file from youtube or find it in a browser cache directory and play it in mplayer or vlc, i'd expect much better performance). There are some ways to get the acceleration though - nvidia has VDPAU which can be used to offload video playback to gfx card but you need to look for vdpau enabled versions of video players. Also flash offers no way to accelerate its content, though i might have read something that newest 10.2 can be vdpau enabled - i am not sure. You'd have to investigate that on your own.

if the binary blob works for your nvidia, you'll be better off because you get at least a chance to try vdpau :)

EDIT: scratch that.
[http://en.wikipedia.org/wiki/Nvidia_PureVideo](http://en.wikipedia.org/wiki/Nvidia_PureVideo)

Board Name: GeForce 6 series
Core Type: NV4x
PureVideo HD: VP1
**VDPAU feature set: Not Supported**

---


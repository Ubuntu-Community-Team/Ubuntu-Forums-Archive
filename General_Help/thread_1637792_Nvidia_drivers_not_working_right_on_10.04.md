---
title: "Nvidia drivers not working right on 10.04"
date: 2010-12-04
forum: General Help
---

### Post by Rumbl3 on 2010-12-04
EDIT: well i think i figured out the problem. I just did what i did below reinstalled them and seems to be working again. I installed the drivers then updated my ubuntu install (fresh install) which i read in another thread that if something updates the kernel or whatever it seems to below out your nvidia install on 10.04 and 10.10 i think if i remember right.

So anyway problems seems to be fixed will find out when i try to do some gaming :) lol. 



Ok so i haven't been using ubuntu in a very long time. Seen 10.04 lts came out and decided to wander back (xp is just getting to old and seems to be getting more and more sluggish everytime i upgrade to newer and newer hardware lol think no one is really supporting it anymore or barely and i'm to dam cheap to buy 7 lol) 

anyway so i downloaded the newest geforce drivers from nvidia. 

I followed instructions i had seen on here can't find the thread now. 

anyway I shut down nouveau or whatever its called. 

Then i did a alt+ctrl+F1 

cd Desktop

tried using sudo service gdm stop but it don't work
so i did sudo /etc/init.d/gdm stop that worked but recommends the way that won't work above lol least for me.

Then i had the nvidia driver on my desktop so i did sudo sh N (then tab) enter. it started the driver up said it could not install the application or something i forget eh i'll find out but asked if i would like to continue. I said yes and installed the driver everything seems somewhat ok after that then i restart my machine and bam says i'm in low graphics mode now, and my x-server for nvidia don't have any options in it at all to modify anything....

I'm using NVIDIA-Linux-x86-260.19.21.run
Nvidia driver i have should i try the older one? if i can find it 250 something i think it was?

Just curious if there is another method i can try to get a driver in. I don't like using old drivers i tend to like the hot new stuff either beta or latest solid release. 

SO any suggestions thx rumbl3!

---

### Post by efflandt on 2010-12-05
You are making things too complicated for yourself.  You should have just gone to System > Administration > Hardware Drivers, activate nvidia, then reboot.  That would have set up a default xorg.conf for you.

The step you are probably missing is that you have not done **sudo nvidia-xconfig** to set up xorg.conf.  But before you do that you need to stop gdm (**sudo stop gdm** should work), then after the nvidia-xconfig reboot (**sudo shutdown -r now**).

I don't even think you need the latest drivers for your video card if your computer is getting old and you have had the video card for awhile.  So whatever is the nvidia-current version in Ubuntu probably would have worked if you hadn't started tampering with things.

---


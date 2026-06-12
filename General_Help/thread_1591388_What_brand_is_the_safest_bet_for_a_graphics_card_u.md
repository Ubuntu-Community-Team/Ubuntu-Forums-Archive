---
title: "What brand is the safest bet for a graphics card upgrade?"
date: 2010-10-09
forum: General Help
---

### Post by Macfunky on 2010-10-09
I want to do research into which graphics card is going to work best with my computer. I am looking for a PCI graphics card for modest use with Ubuntu 10.04. I am not a gamer so i won't be looking for anything too intensive and i don't want to spend a huge amount. Currently i am using the computers onboard graphics and it's not 100% up to scratch so i am wondering what brand should i look at? I don't want to assume anything but i would imagine more generic cards would have a better chance of working than something new, powerful and more cutting edge? I do only want something that will allow my computer to run more smoothly. Anyone have any ideas of what would be best for me to research and which brands should give me the least hassle? Cheers.

---

### Post by timgood on 2010-10-09
In my opinion, Nvidia cards seem to be the best supported in Linux - and you have the choice of the open or closed source drivers to choose from after installation. The 9600 series are relatively inexpensive and run very well under Ubuntu, giving you good eye-candy and 3D acceleration. YMMV!

Hope this helps.

---

### Post by Maximus_ARNP on 2010-10-09
I agree with TimGood. Definitely not ATI.

---

### Post by dcstar on 2010-10-09
> **Maximus_ARNP said:**
> I agree with TimGood. Definitely not ATI.

I have had far less issues with my ATI video hardware since changing from Nvidia in my previous computer (which I used specifically for Ubuntu support).

There are still bug reports re mouse clicks failing on Nvidia hardware that have been ongoing for years - as soon as I went to ATI this issue disappeared for me.

Unfortunately both these hardware families are at the mercy of the vendor drivers for full support, and new cards/chipsets will usually have to wait for updated kernels and/or drivers.

The OP also has Ubuntu 8.10 listed, there may be issues with such an old version as well with any new video card.

---

### Post by andyvy on 2010-10-10
Hardware is almost the same when comparing ATI & nVidia. nVidia linux driver updates are more frequent and are more stable from my experience, but that doesn't mean ATI won't run at all. If you're fairly new @ Linux go with nVidia for less problems. If you're experienced you can go with either ATI or nVidia.

Brand names, I've had good luck with PNY, BFG & Sapphire cards, both ATI & nVidia.

Currently I'm using nVidia 8800GTX 1GB made by PNY, never had any issues. Even runs new games likes Starcraft 2 at almost highest settings under wine. My card was on NewEgg for around 130-160$ few months back I believe. I paid 400$ for it around 4 years ago. (Even typing out the price difference hurt just now).

---

### Post by formaldehyde_spoon on 2010-10-10
+1 for nvidia.

---

### Post by CharlesA on 2010-10-10
I've always used Nvidia cards, but I don't recall any problems on machines running ATI.

---

### Post by timgood on 2010-10-10
> **dcstar said:**
> I have had far less issues with my ATI video hardware since changing from Nvidia in my previous computer (which I used specifically for Ubuntu support).

There are still bug reports re mouse clicks failing on Nvidia hardware that have been ongoing for years - as soon as I went to ATI this issue disappeared for me.

I had exactly the opposite experience - after years of suffering corrupted displays and random crashes with an ATI card, all disappeared when I changed to NVidia. I have never had a problem with mouse clicks failing, and have been using NVidia with Linux for over 4 years now.

If you're thinking of using your computer as a media streamer or attaching it to a TV, then also remember that XBMC standalone supports NVidia much better than ATI. But horses for courses - I'm sure that other people with different hardware and divergent chipsets will have different stories. After all, we're all different. Apart from me, that is, I'm just the same as everyone else. But everyone else is different :).

Hope this helps.

---

### Post by P4man on 2010-10-10
+1 for nvidia.

Always had nvidia, never had any problems in linux. My latest card is an ATI, and I thoroughly regret it. I have the choice between an opensource driver with really bad 3D performance and causing my fan to go beserk (i have a rather hot ATI card, and the OSS drivers dont support power management), and a closed source drivers thats frequently giving graphical corruption in compiz, troubles with HDMI and/or svideo. I cant even change the default monitor in the ati drivers.

Those who experienced problems with nVidia, I suspect ran older cards that were no longer supported by nvidia, such as geforce 6's.

---

### Post by rolodoom on 2010-10-10
I suggest nVidia cards to. I had problems with ATI.

---

### Post by WorMzy on 2010-10-10
Another +1 for Nvidia. I've been using a 8800GTX for years, and I've never had any problems.

---

### Post by cascade9 on 2010-10-10
I've never had any issues with the nVidia cards I own or have setup for others (everything from very old rivas through to new GTX4XX cards). Apart from the ones that were dead or dying anyway. 

I've also never had any issues with ATI either. More people do seem to have issues with ATI, how much of that is luck, I dont know...and there are people in this thread that have had the opposite problem, so mileage varies. ;) 

I HAVE had issues with Intel, VIA, SiS and a few other obscure brands (Number Nine anyone? LOL). nVidia is probably the safest bet, but going ATI isnt crazy. 

> **P4man said:**
> Those who experienced problems with nVidia, I suspect ran older cards that were no longer supported by nvidia, such as geforce 6's.

What do you mean by 'support'? The 6XXX and new cards all use the same drivers (well, for now anyway) and setting up a GF6XXX is the same process as a newer card with all the distros I've used. 

I guess that if you actually called nvidia for support witha  linux distro, you wouldnt get much help anyway. 

Honestly, I dont know why I've had no issues with ATI/nVidia when so many other people have...luck? skill? experience? sheer "I will not let some dumb collection of silicon beat me"? No idea.....I'm just glad I havent had problems. ;)

---

### Post by P4man on 2010-10-10
> **cascade9 said:**
> 
What do you mean by 'support'? 

I mean that they are no longer supported by the new drivers, but require the nvidia legacy drivers (173 and 93 series). You're right though, I just checked and nvidia  are still supporting even geforce 6s with their latest drivers, which I find impressive given how old it is (6 or 7 years?). A 4 year "young" ATI X1950 is no longer supported by ATI (yes, I realise there are OSS drivers for it).

ANyway, the few problems Ive seen with nvidia cards and linux are usually with old cards no longer supported by current drivers. That mean with really old hardware, geforce FX 5000 series or older.

---

### Post by cascade9 on 2010-10-11
The 6600GT is 6 years old. ;) I'm running one in one of the boxxen around here. I you think that the 6XXX series is old, you should see the riva hanging around here (1997!) 

I havent had any issues with the older cards either, but I havent tried running distros with really new xorg (1.9) versions with the older cards.

---

### Post by SeijiSensei on 2010-10-11
The biggest improvement in NVIDIA cards for me came with the development of [VDPAU]("http://en.wikipedia.org/wiki/VDPAU") which enables media players to offload H.264 decoding to the card's GPU.  VDPAU support is available in the 8xxx series cards and up, though I understand that support in the 8xxx cards is more limited than in later generations.  I have an XTX card with a 9500GT, and it has no trouble handling the KDE plasma desktop or decoding H.264 video streams.  (I do wish Adobe would include VDPAU support in Flashplayer, but that's another story.)  

My next computer may be one of these ION-based "[nettops]("http://www.newegg.com/Product/Product.aspx?Item=N82E16856173005")" so I can hang it off the back of my TV and move the desktop I have connected to it now to my office.

---

### Post by cascade9 on 2010-10-11
> **SeijiSensei said:**
> The biggest improvement in NVIDIA cards for me came with the development of [VDPAU]("http://en.wikipedia.org/wiki/VDPAU") which enables media players to offload H.264 decoding to the card's GPU.  VDPAU support is available in the 8xxx series cards and up, though I understand that support in the 8xxx cards is more limited than in later generations.  I have an XTX card with a 9500GT, and it has no trouble handling the KDE plasma desktop or decoding H.264 video streams. 

Just FYI- yes, the 8XXX series cards was when VDPAU was introduced, but not all 8XXX cards have VDPAU support (320/640MB GTS, 8800GTX and 8800 ultra have no VDPAU). Also, some of the 8XXX cards have better VDPAU features than some of the 9XXX cards (some 8XXX have feature set 'B', all 9XXX cards apart from the 9300 have the lower feature set 'A'). See here for more detail- 

[http://en.wikipedia.org/wiki/Nvidia_PureVideo](http://en.wikipedia.org/wiki/Nvidia_PureVideo)

---

### Post by petrasflorin on 2010-10-11
MSI nVIDIA GTS 250 512 DDD3.
[http://www.priceme.co.nz/MSI-GeForce-GTS250-512MB-DDR3/p-883327888.aspx](http://www.priceme.co.nz/MSI-GeForce-GTS250-512MB-DDR3/p-883327888.aspx)

---


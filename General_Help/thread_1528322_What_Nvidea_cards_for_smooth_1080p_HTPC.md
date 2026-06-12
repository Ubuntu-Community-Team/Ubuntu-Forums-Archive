---
title: "What Nvidea cards for smooth 1080p HTPC?"
date: 2010-07-10
forum: General Help
---

### Post by sastusbulbas on 2010-07-10
Hi all,

Wondering what Nvidea cards offer smooth 1080p playback with Ubuntu? I seem to remember a thread stating cards from a specific model upward doing this better and offering CPU off-loading?

I am considering changing from ATI to Nvidea as it seems this may be an easier option to getting things started with an Ubuntu based HTPC instead of the Windows 7 purchase recommended by others here. Though another recommendation has been Mint?

---

### Post by cascade9 on 2010-07-10
That would be VDPAU. It works for all the nvidia cards 8XXX onward (excpet for the 8800 ultra, 8800 GTX and 8800 GTS 320/640MB models). 

The best cards for VDPAU are the GT220/GT240. They have the biggest 'feature set' (what video formats are decoded by VDPAU). See here-

[http://en.wikipedia.org/wiki/Nvidia_PureVideo](http://en.wikipedia.org/wiki/Nvidia_PureVideo)

---

### Post by sastusbulbas on 2010-07-10
So would the Nvidea 240 with the likes of an Intel E3300 or E5300 be sufficient with 2gb of ram, either DDR400 PC-3500 or DDR2-PC5300?

---

### Post by cascade9 on 2010-07-11
People are playing HD content (via VDPAU) on systems with less power than that- Intel Atoms with 1GB. ;) 

Just FYI, you cant just install the card, teh drivers and then get smooth HD playback, you will need to do some setting up for VDPAU.

---

### Post by sastusbulbas on 2010-07-11
How does one set up VDPAU for HD in an Ubuntu system? Is it more straight forward than trying to configure ATI?

---

### Post by cascade9 on 2010-07-12
Hopw you setup VDPAU depends on your version and what media player you want to use ;)

---

### Post by gradinaruvasile on 2010-07-12
The nvidia 200 series lower versions (210-240, maybe 260) have full VDPAU feature set (C). The GTX versions dont.
I have a Gf 210 (Asus) and it works great with HD movies (~5% CPU on 1080p).
At home i have a 8200 integrated nvidia card on Asus M3N78-VM mobo - it plays perfectly well through VDPAU (it has set B).

PS. On Ubuntu you have to look up the vdpau-enabled drivers PPA + the mplayer vdpau-enabled versions PPA. The driver from the nvidia site (i use it) has everything bundled and it straightforward to install.

 On Debian Squeeze the software setup is more simple - install driver + the vdpau-driver package from the main repos (or use the nvidia-provided .run package to install the full driver), install smplayer from the multimedia repo (set output to vdpau from the menu), play HD movie.

---

### Post by cascade9 on 2010-07-12
> **gradinaruvasile said:**
> The nvidia 200 series lower versions (210-240, maybe 260) have full VDPAU feature set (C). The GTX versions dont.
I have a Gf 210 (Asus) and it works great with HD movies (~5% CPU on 1080p).
At home i have a 8200 integrated nvidia card on Asus M3N78-VM mobo - it plays perfectly well through VDPAU (it has set B).

Depends on what GTX you are talking about. 

8800GTX- no VDPAU
GTX260-295- feature set 'A'
GTX460-480- feature set 'C'. 

[http://en.wikipedia.org/wiki/Nvidia_PureVideo](http://en.wikipedia.org/wiki/Nvidia_PureVideo)

That said, a 8800GTX, GTX2XX or GTX4XX aren't good cards for people who arent gamers.

---


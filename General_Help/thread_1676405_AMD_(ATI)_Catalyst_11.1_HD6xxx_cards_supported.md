---
title: "AMD (ATI) Catalyst 11.1 HD6xxx cards supported?"
date: 2011-01-27
forum: General Help
---

### Post by BrokeMahPC on 2011-01-27
AMD (ATI) Catalyst 11.1 for linux now out with a listing for HD6xxx series cards.
[http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)

I guess this means my HD6850 is now supported in Linux - anyone tried the driver yet?
Not sure about other cards as there is nothing in the release notes apart from install instructions

Also there were lots of xorg updates plus a kernel update for Ubuntu 10.10 over the last few days.

Does anyone know if we can activate the administration - hardware drivers yet? Or is the only option to download the above?

edit--------------
6xxx NOT fully supported - see below - you still have to hack the watermark and edit xorg as with 10.12

---

### Post by Rapture2k4 on 2011-01-27
I am battling this issue now. It doesn't appear to support it. This really sucks. Everything is amazingly pretty in Windows though. Makes me wish I had bought a 5770 instead.

I can install the driver fine, but aticonfig reports no supported adapters found. I added "ATI radeon 6850" into xorg.conf, but now I get a nice little watermark (which I know I can remove) saying it is unsupported.

So much for an "upgrade" from my 8800GTS...

---

### Post by flebbelep on 2011-01-27
hm, same here, I have installed catalyst 11.1 on my pc with a hd6870, but I still get the message No supported adapters detected from aticonfig

---

### Post by Rapture2k4 on 2011-01-27
I've looked, but I can't find anything on AMD's site about supported cards in Linux for 11.1. Did I miss something?

---

### Post by BrokeMahPC on 2011-01-27
"Sounds of loose objects being thrown around office and head banging on desk!!!!"

It's just wonderful:
Jockey wants you to install drivers for HD 6xxx and they don't work!
Now AMD wants you to install drivers and they dont work either!

I was doing 90% of my work on Ubuntu but another month of this and I will finally be going out and buying Windows 7.

This video driver nonsense has been going on far too long. I heartily reccomended Linux to friends and family only for them to be left infuriated by the Kernel Mode Setting fiasco and video driver problems.

Look ubuntu guys and gals - THE SCREEN HAS GOT TO WORK!
It's the most basic fundemental thing. Without that this is not a real OS.
People don't want to spend hours tweaking things and following complex methodology to install and uninstall an array of drivers that often leave the system borked.

If only you didn't have to paw through hundreds of pages of forums and bad documentation just to glean the merest hint of advice - much of it wrong or obsolete.

It's elephant in the room that no one wants to talk about. I am tired of flipping between Windows and Ubuntu because things stopped working in 10.04. all video driver related I might add.

---

### Post by BrokeMahPC on 2011-01-27
> **Rapture2k4 said:**
> I've looked, but I can't find anything on AMD's site about supported cards in Linux for 11.1. Did I miss something?

Could not find it either - maybe they don't know, if things aren't progressing as planned or FUBAR people often do not want to admit it. The lack of advice or documentation from official source - Ubuntu or AMD says something to me.

edit---------------------------------
Just found this on the wiki:
**Cards in this group are unsupported as of Catalyst 10-12. The Catalyst  driver may run on these cards, but it is not guaranteed (and you will be  stuck with an "Unsupported Hardware" watermark unless you hack the  control file). Full open source support is forthcoming in Linux kernel  2.6.38.**
[B]* CAICOS      Radeon HD 6350
* TURKS       Radeon HD 6670
* BARTS       Radeon HD 6850/6870
* CAYMAN      Radeon HD 6950/6970[/B]

So I guess it's not surprising..............when is 2.6.38 coming out? I might have a go at compiling it.

yet another edit-----------
Kernel 2.6.38 will ship with Natty in April - 3 months to wait. 2.6.38 is in the repo's at release candidate 2 (rc2) stage.

---

### Post by flebbelep on 2011-01-27
hm, I got it to work it seems, I used this page: [http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Restricted_Drivers_Manager](http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Restricted_Drivers_Manager)
now I can use the native resolution of my monitor, and 3d support is enabled.
The only irritating thing is the unsupported hardware watermark in the corner, but I am trying to remove that watermark.

---

### Post by Rapture2k4 on 2011-01-27
BrokeMahPC,

My thoughts exactly. I've forced myself to use Linux for work and am now realizing why the military refuses to use it as a main OS. As a technician, my time is better spent helping active duty members instead of begging on forums/IRCs.

I love the concept of Ubuntu. I find that when it comes to software, everything is better (the price doesn't hurt either). When it comes to hardware on the other hand... well, need I say more? When it comes to server uses, I don't think Linux can be beat. I still find myself spending way too much time tweaking it for Window's based architectures and networking (LDAP, Samba, etc) though.

I think I'm just going to use Ubuntu under VM from now on. Resolves all my hardware complaints and I've got a beefy enough system to handle 5-6 VMs at a time.

As far as the 6850 goes (or any new hardware that WILL be popular), I would like to see devs working with big companies with their evaluation models before they hit mainstream. I hope this can be patched before April. I was just starting to get used to Blender and Gimp. Now Blender takes a crap every time I boot it :(

---

### Post by aliceme on 2011-01-27
Hi

The AMD Catalyst 11.1 display drivers seems not available for those running Ubuntu 10.10 with Radeon HD 6900, 6900 series graphics cards installed yet.

Source from: 
[http://www.downloadatoz.com/driver/articles/ati-catalyst-11-1-linux-display-driver-for-ubuntu-10-10-update-download.html](http://www.downloadatoz.com/driver/articles/ati-catalyst-11-1-linux-display-driver-for-ubuntu-10-10-update-download.html)

---

### Post by BrokeMahPC on 2011-01-28
> **aliceme said:**
> Hi

The AMD Catalyst 11.1 display drivers seems not available for those running Ubuntu 10.10 with Radeon HD 6900, 6900 series graphics cards installed yet.

Source from: 
[http://www.downloadatoz.com/driver/articles/ati-catalyst-11-1-linux-display-driver-for-ubuntu-10-10-update-download.html](http://www.downloadatoz.com/driver/articles/ati-catalyst-11-1-linux-display-driver-for-ubuntu-10-10-update-download.html)
The article you link to does not mention any 6xx cards so no idea what you mean.
AMD offers the drivers to you on the AMD website if you put 6xxx in the field? How are we supposed to know what's supported and what's not without proper release notes? At the very least it should say 6xxx cards not supported yet. Or partially supported (I'm still not sure if it works 100% - why the Unsupported HardWare watermark?)

[IMG]http://img193.imageshack.us/img193/4253/screenshotamdgraphicsdr.png[/IMG]

---

### Post by ste_bran on 2011-02-10
> **BrokeMahPC said:**
> The article you link to does not mention any 6xx cards so no idea what you mean.



doesn't mention??? The line he quotes about 6900 cards comes directly from the article he links to.

I sent a msg to the Linux Crew asking if 69xx is supported.

---

### Post by nico_demo on 2011-02-13
> **flebbelep said:**
> hm, I got it to work it seems, I used this page: [http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Restricted_Drivers_Manager](http://wiki.cchtml.com/index.php/Ubuntu_Maverick_Installation_Guide#Restricted_Drivers_Manager)
now I can use the native resolution of my monitor, and 3d support is enabled.
The only irritating thing is the unsupported hardware watermark in the corner, but I am trying to remove that watermark.
Great link, thanks so much! 
Any luck removing the watermark?

---


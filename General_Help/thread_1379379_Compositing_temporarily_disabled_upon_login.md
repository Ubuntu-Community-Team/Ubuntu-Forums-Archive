---
title: "Compositing temporarily disabled upon login"
date: 2010-01-12
forum: General Help
---

### Post by corevette on 2010-01-12
Every time I login, compositing is disabled. I have to manually go into settings and Desktop and press 'resume compositing.' When I press it, it says: "compositing has been suspended by another application, press alt+shift+f12 to resume." So if i press the key combination, of course it does resume, but i have to go through this process every time i start the computer.  here's my xorg.conf:

> Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

I'm running Kubuntu 9.10 64 bit edition.

Here is my graphics card
[http://www.newegg.com/Product/Product.aspx?Item=N82E16814102853](http://www.newegg.com/Product/Product.aspx?Item=N82E16814102853)

I've installed the latest drivers

---

### Post by oliverheard on 2010-03-27
I'm having the exact same problem. Did you manage to solve it on your end? Anyone else have info on this?

---

### Post by nickbnf on 2010-03-28
Seems to be a known issue with ATI's fglrx driver. The only workaround I've found is to "Disable functionality checks" in "System Settings->Desktop Effects->Advanced", it then works properly! Still don't know why we need to do that though...

---

### Post by julio_cortez on 2010-05-07
I was about to open a new discussion to post this, when I found this.

Unfortunately also I have the same problem with my HD5770 and I also got to the same conclusion too. No version of fglrx is working properly for some obscure reason.

What is strange is that compositing sometimes worked in Kubuntu Karmic (at startup sometimes compositing worked, sometimes it didn't) but it doesn't work at all in Lucid: each and every time I boot to Lucid I have to resume compositing manually (which isn't that big deal but indeed it's a bit annoying).

I've tried updates from 10.1 to 10.4 of the ATI driver (always downloaded from their site) and never seemed to solve this problem.
Plus I've tried to get the latest fglrx via apt-get (hoping something different would happen) but still had no joy.

I'll try disabling the functionality check by the way.. Thank you for the suggestion!! ;)

---

### Post by yoshimitsuspeed on 2010-05-14
> **corevette said:**
> Every time I login, compositing is disabled. I have to manually go into settings and Desktop and press 'resume compositing.' When I press it, it says: "compositing has been suspended by another application, press alt+shift+f12 to resume." So if i press the key combination, of course it does resume, but i have to go through this process every time i start the computer.  here's my xorg.conf:



I'm running Kubuntu 9.10 64 bit edition.

Here is my graphics card
[http://www.newegg.com/Product/Product.aspx?Item=N82E16814102853](http://www.newegg.com/Product/Product.aspx?Item=N82E16814102853)

I've installed the latest drivers

I'm having the same problem after upgrading to 10.04. 
Worked fine in 9.10 but no longer. 
Here's my thread.
[http://ubuntuforums.org/showthread.php?t=1470642](http://ubuntuforums.org/showthread.php?t=1470642)

---

### Post by jonas_t on 2010-05-31
I'm having the exact same problem with an ATI Radeon HD 2400 PRO. Annoying...

Has anybody filed a bug report yet?

edit: on my notebook, running an nvidia card, compositing works just fine...

---

### Post by jonas_t on 2010-05-31
to answer my own question: yes, there already is a bug report on launchpad:

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/552509](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/552509)

---

### Post by AndrewGarib on 2010-07-01
I disabled the functionality checks and compositing works fine on restart. That's on Kubuntu LL with fglrx 2:8.723.1-0ubuntu4 amd64 (which, I assume, is the latest driver).

I wish I read this thread in April.

Nice n pretty now.

---

### Post by yoshimitsuspeed on 2010-07-03
Ok I think I have found a solution.

As far as I can tell this is a problem between Nouveau and the proprietary Nvidia driver. I'm a little pissed they implemented this Nouveau thing so far before it was ready. 
Anyway uninstalling Neauveau is not enough. 
I had to blacklist it as explained in this thread.
[http://ubuntuforums.org/showthread.php?t=1519849&highlight=nouveau](http://ubuntuforums.org/showthread.php?t=1519849&highlight=nouveau)
Before that I was getting the same fault he did when trying to install a Nvidia driver direct from Nvidia.
The repo version installed but caused all these problems.
Once I did
```
sudo apt-get --purge remove xserver-xorg-video-nouveau
```

Then

> **HomeSlixe said:**
> try this in terminal  ```
sudo nano /etc/modprobe.d/blacklist.conftv 
``` Add these:


blacklist vga16fb
blacklist nouveau
blacklist rivafb
blacklist nvidiafb
blacklist rivatv

Then...

ctrl O to write
crtl X to quit

[CODE]sudo apt-get --purge remove nvidia-*


Then deleted my xorg.conf 
I restarted and entered console and installed Nvidias current version I had downloaded. Nvidia currently has a newer version than the repos.

Nvidia-current might work as well after blacklisting Neauveau, I'm not sure since I didn't try it.

However after doing all that and installing Nvidias 256.35 driver I haven't had a problem. 
Compositing has been fine, VLC, etc, even google earth works now. 
Pretty much all the graphics troubles I was having are gone. 

I'll update my thread if anything funky shows up.

This could at least help Nvidia users. Not sure about those having ATI trouble.

---

### Post by schnelle on 2010-07-03
I am using fglrx and "Disable functionality checks" in System Settings->Desktop Effects->Advanced works for me.

---

### Post by kolzene on 2010-11-16
I also had the same problem, found this thread, and tried the "Disable functionality checks" thing, and it worked as well! I'm using 10.04 Kubuntu, with the Radeon closed driver. 

Thanks!

---


---
title: "RADEON HD 4350 on ubuntu 10.04 LTS (help)"
date: 2010-06-28
forum: General Help
---

### Post by MasterNeo on 2010-06-28
Hello everyone, 
I have a big problem which can't solve three days and nights :confused:
so...... I decide go out from windows and go to ubuntu, but...
 I Download Ubuntu 10.04 LTS , installed , and got message about
hardware and about activate FGLRX , ok i activating, restart pc, and here
showing to me Boot screen (purple ubuntu) and nothing happens.... like stuck 
and resoliution are about 640 x480 ....... O.o  ok rr pc reinstall os....
next didnt activate FGLRX but go to ati/amd official website and downloaded drivers for linux x86 
installed ,,,,in systems > preferenses  appeared mmm i thin two catalyst options one simple another administrate or... dont remember ,,,whatever...  rr pc and again when booting, come Purple screen ubuntu in about resoliution 640x480 and nothing..... again rr pc and reinstaling os..... . 
[B]sry for my bad english but maybe can help me to solve this problem
...waiting answers,,,  ;)[/B]

---

### Post by MasterNeo on 2010-06-28
any ideas from radeon hd owners? :confused:

---

### Post by Yarui on 2010-06-28
Is this a problem you are having after completing the installation or while trying to start the install process?  Can you successfully run the OS Live from the CD?

---

### Post by XSAlliN on 2010-06-28
**FGLRX is _still_ junk**, you should stick with integrated Open Source drivers. I use those with my HD 4850 and most of the essential stuff works (like 2D/3D acceleration). Yet with FGLRX I get the eternal tearing problems caused by VSync.

---

### Post by Yarui on 2010-06-28
> **XSAlliN said:**
> **FGLRX is _still_ junk**, you should stick with integrated Open Source drivers. I use those with my HD 4850 and most of the essential stuff works (like 2D/3D acceleration). Yet with FGLRX I get the eternal tearing problems caused by VSync.
You are able to use 3d acceleration with the open source drivers on an HD 4850?  The documentation says that Radeon HD 4xxx and Radeon HD 3xxx cards don't have 3d acceleration.  Has that changed or is that just with specific cards from those series?

---

### Post by QIII on 2010-06-28
Catalyst works fine for me on all of my AMD/ATI machines.  It can be installed from the repos.

Install the Admin version of Catalyst Control Center.

Tearing can generally be taken care of by adjustments in CCC, or by simply turning off Compiz temporarily.

I haven't gotten 3D to work with the open source driver.  I'd be interested in hearing how you got that to work.

---

### Post by MasterNeo on 2010-06-28
> **QIII said:**
> Catalyst works fine for me on all of my AMD/ATI machines.  It can be installed from the repos.

Install the Admin version of Catalyst Control Center.

Tearing can generally be taken care of by adjustments in CCC, or by simply turning off Compiz temporarily.

I haven't gotten 3D to work with the open source driver.  I'd be interested in hearing how you got that to work.

...and admin version can download install from where?


**Yarui** live cd working and all copies working :)
after install all working, everything crashed after i install ati drivers or activate fglrx ;)__

---

### Post by Yarui on 2010-06-28
Oh, okay, I actually had a similar problem when I first installed 10.04.  After messing with my video drivers everything got kind of screwed up.  When I restarted I had an option of booting into a low graphics mode, though.  I did that and uninstalled and reinstalled the fglrx package and then everything started working right.

---

### Post by QIII on 2010-06-29
The Catalyst Control Center installs the Admin version and the non-admin  version, it turns out.

Look in Synaptic to fglrx-amdcccle.

When you say you activated the driver, did you issue the following in the terminal

```
sudo aticonfig --initial
```

and then either shut down (best idea in my experience) or issue

```
sudo service gdm restart
```

---

### Post by MasterNeo on 2010-06-29
tryed to all those things but nothing, rr pc after install drivers and ubuntu boot screen crashed in horoble resoliution..and do nothing :(

---

### Post by MasterNeo on 2010-06-29
p.s. i today in morning tryed and another version, download from ati official linux x86 driver
**sudo sh  ./ati-driver-installer-10-6-x86.x86_64.run**
```
Created directory fglrx-install.sVFDbx
Verifying archive  integrity... All good.
Uncompressing ATI Catalyst(TM) Proprietary  Linux  Driver-8.741.........................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================
Detected  configuration:
Architecture: i686 (32-bit)
X Server: X.Org 7.5
Removing  temporary directory: fglrx-install.sVFDbx
```

then [B]sudo aticonfig --initial
[/B]```
Found fglrx primary device section
Using /etc/X11/xorg.conf
Saved  back-up to /etc/X11/xorg.conf.fglrx-0
```

everything seems ok , in system> preference appear two ATI CATALYST CONTROL CENTER
but cant open (Initialization error) :
[I]There was a problem initializing   Catalyst.......It could be caused by the following. No  ATi graphic  driver is installed, or the ATI driver is not functioning
properly.  Please install......................or configure using aticonfig  
[/I][B]
cat /etc/X11/xorg.conf[/B][I] and:

[/I]```
Section "ServerLayout"
   Identifier      "aticonfig Layout"
   Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section  "Files"
EndSection

Section "Module"
EndSection

Section  "Monitor"
   Identifier   "aticonfig-Monitor[0]-0"
   Option        "VendorName" "ATI Proprietary Driver"
   Option       "ModelName"  "Generic Autodetecting Monitor"
   Option       "DPMS" "true"
EndSection

Section  "Device"
   Identifier  "aticonfig-Device[0]-0"
   Driver       "fglrx"
   BusID       "PCI:2:0:0"
EndSection

Section  "Screen"
   Identifier "aticonfig-Screen[0]-0"
   Device      "aticonfig-Device[0]-0"
   Monitor    "aticonfig-Monitor[0]-0"
    DefaultDepth     24
   SubSection "Display"
      Viewport   0 0
       Depth     24
   EndSubSection
EndSection
```in next step i write:
```
ubuntu@AMD64:~$ fglrxinfo
Segmentation fault
```

and done , ofcourse if i restart pc then will crashed again.
now i dont restart pc, and wait another version for solving this problem

---

### Post by The Explanation on 2010-07-01
I am having the exact same problem. Whenever I install the proprietary ATI driver using jockey, the system fails to start and locks on the splash screen and is in horrible resolution. I have to restart in failsafe graphics to fix it. Also, while running the default open source driver, the edges of the screen (taskbar area) are cut off from view. The machine I am running is an HP m7640n with a Radeon 4350, Western Digital Caviar Green 1TB and Sony Blu Ray drive added connected to a 50" Panasonic plasma (1080p).

I found this link with a similar issue, I don't know if it will help any of you figure it out:
[http://antiflash.org/notes/computers/linux,_radeon_4350_and_hdmi/](http://antiflash.org/notes/computers/linux,_radeon_4350_and_hdmi/)

Meanwhile, I'm going to try manually installing the proprietary driver to see if that fixes it. Any solutions would be greatly appreciated! Also, I don't mind which driver is used, so long as it works. However, I plan on hopefully playing back blu rays on it eventually, and I'm assuming the proprietary driver would be much more effective for this.

---

### Post by MasterNeo on 2010-07-02
yeah, maybe in 10.10 version will work, anyone solve it 
hope  remains

---

### Post by Yarui on 2010-07-03
> **MasterNeo said:**
> yeah, maybe in 10.10 version will work, anyone solve it 
hope  remains

I disagree, this isn't likely an issue with Ubuntu, but an issue with the driver.  A new release is unlikely to solve this issue.

---

### Post by cloyd on 2010-07-03
I had problems with different radeon card . . . symptoms were not the same, but display would go crazy after 40-50 minutes. This link cured it. I found this not by looking for exact same problem, but looking for issues related to plymouth.   It just got rid of the splash screen, and display has not acted up since.

  	 	 	 	 	 	  [COLOR=#000080]_[http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml](http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml)_[/COLOR]
 
some others here might share their comments on this. If it won't work for you, then try something else. It helped me.

---

### Post by alienkid10 on 2010-07-03
I am running a 4350 with FGLRX and everything is fine.

---

### Post by noelferreira on 2010-07-18
Hi.

I'm having the exact same problem with that card using amd64. Did you already found a solution for it.

Thanks,

noel

---

### Post by noelferreira on 2010-10-15
Hi. 

I have recently updated my system to 10.10 and the problem persists.
Please let me know if you have some solution for this problem.

Thanks,

noel

---

### Post by Yarui on 2010-10-16
Since this topic kind of died back when it was active and it was never marked as solved, I'm going to guess that no one was able to resolve this problem.  Unfortunately I think support for Radeon cards in linux is just not very good, so if you end up having some seemingly unsolvable problem like this, it probably actually is pretty much unsolvable.

I finally got sick of all the problems my Radeon card was causing me and just bought an nvidia card to replace it.  I'm not suggesting this is what you should do, I'm just saying that I was never able to solve my problems either and I finally just decided to take the easy way out.

---


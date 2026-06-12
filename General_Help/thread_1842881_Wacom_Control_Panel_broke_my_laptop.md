---
title: "Wacom Control Panel broke my laptop"
date: 2011-09-12
forum: General Help
---

### Post by jlh68 on 2011-09-12
I downloaded Wacom Control Panel application from:  [http://gtk-apps.org/content/show.php/Wacom+Control+Panel?content=104309](http://gtk-apps.org/content/show.php/Wacom+Control+Panel?content=104309).

When I restarted my computer it would not boot completely.  It would boot part of the way and then just h=get hung up and never competer the boot.

I would like to revert to my OS prior to this down load.  How do I return to a previous boot image?  Or can I reinstall Ubuntu 10.10?  I have a separate partition for my OS.

Please provide instructions on removing app and/or getting my system back to a working image.

---

### Post by Favux on 2011-09-12
Hi jlh68,

Good question.  Did you install it through its PPA?  There is a script out there called PPA-purge to remove PPA's.

Failing that since the install commands are:
```
sudo add-apt-repository ppa:hughescih/ppa && sudo apt-get update && sudo apt-get install wacom-utility
```
couldn't you just use apt-get to remove wacom-utility?  Since it is presumably a configuration file that is breaking X you'd want *purge* instead of *remove*, so:
```
sudo apt-get purge wacom-utility
```
You'd run that once you got to the command line by using the Recovery Mode option when you boot.  Then reboot.

Then once X has started and you're back in the Desktop again remove the PPA from the repositories.

---

### Post by jlh68 on 2011-09-13
Thanks for the suggestion.  I tried it and unfortunately I have the same problem. Here is my log file showing some other problems. Here is a screen shot of the X-org-0 log file.

---

### Post by Favux on 2011-09-13
From the Xorg.0.log it appears the xorg.conf has the video set up incorrectly.  So you should be able to get to the command line in Recovery Mode OK, you just can't start X.

With Maverick you might not even have an xorg.conf with a default install, depending on your video chipset.  The Wacom Control Panel might have installed one incorrectly and broke X.  I know it used to play with the xorg.conf, because an old version broke my careful Wacom configuration in xorg.conf.  Do you know if you had one before you installed the WCP?  If you made a back up of it all you may need to do is restore from the backup.  If you can post the contents of the xorg.conf.

To determine your video chipset:
```
lspci | grep VGA
```

---

### Post by jlh68 on 2011-09-13
:DI I sure wish I knew more about operating systems.  I used the safestart mode, and decided to use back-up conf file, then restarted and now I am back in business.  Basicly I just hunted around in the safestart mode until I found something that I thought might work.  

I did this before reading your last post, but your last post was "right-on" and would have gotten me to a good boot.

I also thought that the output was to another screen, rather than the laptop screen.

Again, I appreciate your help in this, you gave me some specific directions that got me part of the way, and other directions that made me think my way back.  Now I know why I like a Linux OS over others.  It is fixable, and that is really nice, rather than having to do a clean install.:D

---

### Post by Favux on 2011-09-13
Great!  :)

Although you still might want to look at the xorg.conf.  If it wasn't a back up you made and instead was a failsafe xorg.conf you might be on a VESA video driver rather than a better one for your video chipset.

---

### Post by jlh68 on 2011-09-13
**Favus**: how do I check the drivers for the video in the xorg.conf file?

I have looked at xorg.conf file.  The image is what I get when I search for xorg. In all of them I don't see the VESA driver reference.

My laptop uses mostly Intel chips, except for WiFi and Blue tooth.

---

### Post by Favux on 2011-09-13
The xorg.conf file is at /etc/X11.  You can just navigate there with Places (Nautilus) and open it up in Text Editor.  Copy and paste the contents into a code box, which is the # (above right).

With Intel you might not have a xorg.conf with a default install.  They are trying to make everything more automatic.  If you had the Nvidia proprietary driver for example, it does create an xorg.conf.

Did you run the lspci command I showed in a previous post in a terminal?  If so go ahead and post that too.

By the way what we're you trying to configure on your Wacom tablet?  Which one do you have?

---

### Post by jlh68 on 2011-09-14
> john@NightHawk:~$ lspci
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 12)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 12)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
01:00.0 Ethernet controller: Atheros Communications AR8151 v1.0 Gigabit Ethernet (rev c0)
02:00.0 Network controller: Broadcom Corporation BCM43225 802.11b/g/n (rev 01)
7f:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)

From my lspci | grep VGA
> john@NightHawk:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 12)


It looks like my system is OK.  
Thanks a lot for your help.  I have done some of this before but a year ago or so, therefore it is hard to remember what I had done in the past.

I have a Bamboo Fun 4X6 and I was trying to get the buttons to do something. I was try to get the stylis, eraser, and stuff set up.  The Bamboo works fairly well with *My Paint* application.  I have not tried the GIMP with it.  I have found my Bamboo Fun works plug-n-play with both Ubuntu 10.04LTS and 10.10.  I have not gone to 11.04, or 11.11beta yet, but I have tried to use them "live" CD. I am not sure how I like Unity.

---

### Post by Favux on 2011-09-14
You can also see your xorg.conf by entering in a terminal:
```
gedit /etc/X11/xorg.conf
```
To edit it you would use:
```
gksudo gedit /etc/X11/xorg.conf
```
Before you ever edit it be sure to make a backup.  Here's a fragment of an old xorg.conf with an old intel video chipset:
```
Section "Device"
	Identifier	"Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
	Driver		"intel"
	BusID		"PCI:0:2:0"
        #Nirea
	#Option "AccelMethod" "exa"
	#Option "MigrationHeuristic" "greedy"
	#Option "ExaNoComposite" "true"
        #Option "FramebufferCompression" "false"
	#Option "Tiling" "false"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	Option		"DPMS"
	HorizSync	31.5-90
	VertRefresh	50-90
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
	Monitor		"Configured Monitor"
	DefaultDepth	24
        SubSection "Display"
          Depth 24
          Modes "1024x768"
        EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection
```

I don't blame you.  I think of Unity in Natty as a beta.  Hopefully some things will be ironed out in Oneiric.  The model should be on the back of the tablet and you can get the product ID by entering *lsusb* in a terminal and looking for the Wacom line in the output.

You can configure the tablet using xsetwacom commands.  That's discussed in the [BambooPT HOW TO]("http://ubuntuforums.org/showthread.php?t=1515562") and there are some sample scripts.  Or you can look at this HOW TO on the Linux Wacom Project's mediawiki:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Tablet_Configuration](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Tablet_Configuration)  And the HOW TO page:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Category:HOWTO](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Category:HOWTO)

---


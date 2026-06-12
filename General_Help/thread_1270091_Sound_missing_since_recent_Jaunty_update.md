---
title: "Sound missing since recent Jaunty update"
date: 2009-09-19
forum: General Help
---

### Post by momist on 2009-09-19
Hi everyone,

Here is *another* "lost sound" thread, but please try to help if you can.  After a recent update to my Jaunty system, I've lost all sound, including the drum roll at boot time.  

I'm using an AMD 1600XP 32 bit processor on a much upgraded homebrew machine which has had the current hardware without sound troubles for a few years now.  The machine can see the on-board C-Media AC'97 'soundcard', as revealed by "hwinfo --sound". ```
19: PCI 02.7: 0401 Multimedia audio controller                  
  [Created at pci.314]
  UDI: /org/freedesktop/Hal/devices/pci_1039_7012
  Unique ID: 1sCg.mUMDO85F5bB
  SysFS ID: /devices/pci0000:00/0000:00:02.7
  SysFS BusID: 0000:00:02.7
  Hardware Class: sound
  Model: "Silicon Integrated AC'97 Sound Controller"
  Vendor: pci 0x1039 "Silicon Integrated Systems Corp."
  Device: pci 0x7012 "AC'97 Sound Controller"
  SubVendor: pci 0x13f6 "C-Media Electronics Inc"
  SubDevice: pci 0x0300 "ECS K7SOM+ motherboard"
  Revision: 0xa0
  Driver: "Intel ICH"
  Driver Modules: "snd_intel8x0"
  I/O Ports: 0xd800-0xd8ff (rw)
  I/O Ports: 0xd400-0xd43f (rw)
  IRQ: 11 (861840 events)
  Module Alias: "pci:v00001039d00007012sv000013F6sd00000300bc04sc01i00"
  Driver Info #0:
    Driver Status: snd_intel8x0 is active
    Driver Activation Cmd: "modprobe snd_intel8x0"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
```
and lspci -v ```
ian@***:~$ lspci -v
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
	Subsystem: C-Media Electronics Inc Device 0300
	Flags: bus master, medium devsel, latency 64, IRQ 11
	I/O ports at d800 [size=256]
	I/O ports at d400 [size=64]
	Capabilities: <access denied>
	Kernel driver in use: Intel ICH
	Kernel modules: snd-intel8x0
```

I don't understand every part of these outputs, for instance what is meant by the Config Status line showing "cfg=new, avail=yes, need=no, active=unknown"?

 I've read and re-read all the various threads about lost sound, and discovered all the variations on volume control and pulse-audio settings etc.  The problem is that none of this software can see the soundcard, as aplay -l shows ```
aplay: device_list:217: no soundcards found...

```

I've read extensively about  /etc/modprobe.d/alsa-base.conf  and tried editing this to make sure the correct codec is used, all to no avail. 

My only option now seems to be to go back to the "image" of the Intrepid setup I was using until recently, and abandon Jaunty entirely.  Before I do that, can anyone suggest something I haven't looked at yet?

Thanks

Ian

---

### Post by oboedad55 on 2009-09-19
> **momist said:**
> Hi everyone,

Here is *another* "lost sound" thread, but please try to help if you can.  After a recent update to my Jaunty system, I've lost all sound, including the drum roll at boot time.  

I'm using an AMD 1600XP 32 bit processor on a much upgraded homebrew machine which has had the current hardware without sound troubles for a few years now.  The machine can see the on-board C-Media AC'97 'soundcard', as revealed by "hwinfo --sound". ```
19: PCI 02.7: 0401 Multimedia audio controller                  
  [Created at pci.314]
  UDI: /org/freedesktop/Hal/devices/pci_1039_7012
  Unique ID: 1sCg.mUMDO85F5bB
  SysFS ID: /devices/pci0000:00/0000:00:02.7
  SysFS BusID: 0000:00:02.7
  Hardware Class: sound
  Model: "Silicon Integrated AC'97 Sound Controller"
  Vendor: pci 0x1039 "Silicon Integrated Systems Corp."
  Device: pci 0x7012 "AC'97 Sound Controller"
  SubVendor: pci 0x13f6 "C-Media Electronics Inc"
  SubDevice: pci 0x0300 "ECS K7SOM+ motherboard"
  Revision: 0xa0
  Driver: "Intel ICH"
  Driver Modules: "snd_intel8x0"
  I/O Ports: 0xd800-0xd8ff (rw)
  I/O Ports: 0xd400-0xd43f (rw)
  IRQ: 11 (861840 events)
  Module Alias: "pci:v00001039d00007012sv000013F6sd00000300bc04sc01i00"
  Driver Info #0:
    Driver Status: snd_intel8x0 is active
    Driver Activation Cmd: "modprobe snd_intel8x0"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
```
and lspci -v ```
ian@***:~$ lspci -v
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
	Subsystem: C-Media Electronics Inc Device 0300
	Flags: bus master, medium devsel, latency 64, IRQ 11
	I/O ports at d800 [size=256]
	I/O ports at d400 [size=64]
	Capabilities: <access denied>
	Kernel driver in use: Intel ICH
	Kernel modules: snd-intel8x0
```

I don't understand every part of these outputs, for instance what is meant by the Config Status line showing "cfg=new, avail=yes, need=no, active=unknown"?

 I've read and re-read all the various threads about lost sound, and discovered all the variations on volume control and pulse-audio settings etc.  The problem is that none of this software can see the soundcard, as aplay -l shows ```
aplay: device_list:217: no soundcards found...

```

I've read extensively about  /etc/modprobe.d/alsa-base.conf  and tried editing this to make sure the correct codec is used, all to no avail. 

My only option now seems to be to go back to the "image" of the Intrepid setup I was using until recently, and abandon Jaunty entirely.  Before I do that, can anyone suggest something I haven't looked at yet?

Thanks

Ian

I have the same controller, Silicon Integrated AC'97 Sound Controller. I had my sound disappear once a while back and the only solution I found after much searching was to reinstall. Haven't had any problems since. If you do decide to reinstall make sure you've got backed up what you want to save. You probably know this, but I like to mention it just in case. Do you know which updates were installed after which your sound took a hike? That might help pin it down.

---

### Post by momist on 2009-09-19
Hi oboedad55,

It has to be something in here:

```
Commit Log for Sat Sep 12 16:57:29 2009


Upgraded the following packages:
gnome-terminal (2.26.0-0ubuntu2) to 2.26.0-0ubuntu2.1
gnome-terminal-data (2.26.0-0ubuntu2) to 2.26.0-0ubuntu2.1
libamrnb3 (7.0.0.2-0.0medibuntu1) to 7.0.0.2-0.1medibuntu1
libgoo-canvas-perl (0.05-1~gscrot1intrepid2) to 0.05-1~gscrot1jaunty1
libpam-modules (1.0.1-9ubuntu1) to 1.0.1-9ubuntu1.1
libpam-runtime (1.0.1-9ubuntu1) to 1.0.1-9ubuntu1.1
libpam0g (1.0.1-9ubuntu1) to 1.0.1-9ubuntu1.1
mencoder (2:1.0~rc2-0ubuntu19) to 2:1.0~rc2-0ubuntu19+medibuntu1
mplayer (2:1.0~rc2-0ubuntu19) to 2:1.0~rc2-0ubuntu19+medibuntu1
mplayer-doc (2:1.0~rc2-0ubuntu19) to 2:1.0~rc2-0ubuntu19+medibuntu1
sun-java6-bin (6-14-0ubuntu1.9.04) to 6-16-0ubuntu1.9.04
sun-java6-fonts (6-14-0ubuntu1.9.04) to 6-16-0ubuntu1.9.04
sun-java6-jre (6-14-0ubuntu1.9.04) to 6-16-0ubuntu1.9.04
sun-java6-plugin (6-14-0ubuntu1.9.04) to 6-16-0ubuntu1.9.04
totem (2.26.1-0ubuntu5) to 2.26.1-0ubuntu5.1
totem-common (2.26.1-0ubuntu5) to 2.26.1-0ubuntu5.1
totem-dbg (2.26.1-0ubuntu5) to 2.26.1-0ubuntu5.1
totem-gstreamer (2.26.1-0ubuntu5) to 2.26.1-0ubuntu5.1
totem-mozilla (2.26.1-0ubuntu5) to 2.26.1-0ubuntu5.1
totem-plugins (2.26.1-0ubuntu5) to 2.26.1-0ubuntu5.1
totem-xine (2.26.1-0ubuntu5) to 2.26.1-0ubuntu5.1
w32codecs (20071007-0medibuntu3) to 20071007-0medibuntu4


Commit Log for Sat Sep 12 17:51:08 2009


Installed the following packages:
libsane-extras (1.0.19.11ubuntu2)


Commit Log for Sun Sep 13 09:11:51 2009


Upgraded the following packages:
firefox (3.0.13+nobinonly-0ubuntu0.9.04.1) to 3.0.14+build2+nobinonly-0ubuntu0.9.04.1
firefox-3.0 (3.0.13+nobinonly-0ubuntu0.9.04.1) to 3.0.14+build2+nobinonly-0ubuntu0.9.04.1
firefox-3.0-branding (3.0.13+nobinonly-0ubuntu0.9.04.1) to 3.0.14+build2+nobinonly-0ubuntu0.9.04.1
firefox-3.0-gnome-support (3.0.13+nobinonly-0ubuntu0.9.04.1) to 3.0.14+build2+nobinonly-0ubuntu0.9.04.1
firefox-gnome-support (3.0.13+nobinonly-0ubuntu0.9.04.1) to 3.0.14+build2+nobinonly-0ubuntu0.9.04.1
libqt4-assistant (4.5.0-0ubuntu4.1) to 4.5.0-0ubuntu4.2
libqt4-dbus (4.5.0-0ubuntu4.1) to 4.5.0-0ubuntu4.2
libqt4-designer (4.5.0-0ubuntu4.1) to 4.5.0-0ubuntu4.2
libqt4-help (4.5.0-0ubuntu4.1) to 4.5.0-0ubuntu4.2
libqt4-network (4.5.0-0ubuntu4.1) to 4.5.0-0ubuntu4.2
libqt4-opengl (4.5.0-0ubuntu4.1) to 4.5.0-0ubuntu4.2
libqt4-qt3support (4.5.0-0ubuntu4.1) to 4.5.0-0ubuntu4.2
libqt4-script (4.5.0-0ubuntu4.1) to 4.5.0-0ubuntu4.2
libqt4-sql (4.5.0-0ubuntu4.1) to 4.5.0-0ubuntu4.2
libqt4-sql-mysql (4.5.0-0ubuntu4.1) to 4.5.0-0ubuntu4.2
libqt4-svg (4.5.0-0ubuntu4.1) to 4.5.0-0ubuntu4.2
libqt4-test (4.5.0-0ubuntu4.1) to 4.5.0-0ubuntu4.2
libqt4-webkit (4.5.0-0ubuntu4.1) to 4.5.0-0ubuntu4.2
libqt4-xml (4.5.0-0ubuntu4.1) to 4.5.0-0ubuntu4.2
libqt4-xmlpatterns (4.5.0-0ubuntu4.1) to 4.5.0-0ubuntu4.2
libqtcore4 (4.5.0-0ubuntu4.1) to 4.5.0-0ubuntu4.2
libqtgui4 (4.5.0-0ubuntu4.1) to 4.5.0-0ubuntu4.2
xulrunner-1.9 (1.9.0.13+nobinonly-0ubuntu0.9.04.1) to 1.9.0.14+build2+nobinonly-0ubuntu0.9.04.1
xulrunner-1.9-gnome-support (1.9.0.13+nobinonly-0ubuntu0.9.04.1) to 1.9.0.14+build2+nobinonly-0ubuntu0.9.04.1


Commit Log for Tue Sep 15 08:34:59 2009


Upgraded the following packages:
libc6 (2.9-4ubuntu6) to 2.9-4ubuntu6.1
libc6-dev (2.9-4ubuntu6) to 2.9-4ubuntu6.1
libc6-i686 (2.9-4ubuntu6) to 2.9-4ubuntu6.1
libopenexr6 (1.6.1-3ubuntu1) to 1.6.1-3ubuntu1.9.04.1
libssl0.9.8 (0.9.8g-15ubuntu3.2) to 0.9.8g-15ubuntu3.3
openssl (0.9.8g-15ubuntu3.2) to 0.9.8g-15ubuntu3.3
tzdata (2009l-0ubuntu0.9.04) to 2009m-0ubuntu0.9.04
tzdata-java (2009l-0ubuntu0.9.04) to 2009m-0ubuntu0.9.04



```

. . . but just what, I can't see.  My Jaunty was an in-situ upgrade from Intrepid.  I have a Jaunty disk that I could do a clean install with, or I can go back to the Intrepid image I took of the root partition (home is separate) before doing the upgrade.

---

### Post by momist on 2009-09-20
OK, so I've done a clean install of Jaunty.  I carefully edited out all the updates that affect sound and applied the rest first, then the sound ones.  Then I had to set up the repositories and refresh my package list from the old one, and weed out every extra package that might break the sound (e.g. gxmms) and it all seems to work.

So I'm marking this thread [SOLVED] - although I never found out what broke the sound.

---


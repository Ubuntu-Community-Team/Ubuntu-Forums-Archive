---
title: "Laptop built in speakers, not working properly"
date: 2010-04-24
forum: General Help
---

### Post by b3n0 on 2010-04-24
Hey all,

I've just finished installing Ubuntu 9.10 64bit on my laptop. The laptop has an Altec Lansing 2.1 built in speaker system. Only the (small) sub on the bottom of the laptop seems to be working. I've noticed that Ubuntu hasn't detected it in the hardware module. The laptop is a HP dv7-3105 tx.

Thanks for your help.

---

### Post by lidex on 2010-04-24
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert these lines at the bottom:
```
options snd-hda-intel model=hp-m4 enable=1 index=0
options snd-hda-intel enable_msi=1 
```
Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```
Press F6 to select the correct soundcard.
Press F3 to show playback levels. F4 selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels.
Go to "System>Preferences>Sound" and make sure the correct soundcard is default

No joy? Go here and install the alsa-backports:
[https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats]("https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats")

---

### Post by b3n0 on 2010-04-24
Thanks mate!

I also just found this, which also seems to do the job.
```
cd ~
mkdir src
cd src
mkdir alsa
cd alsa
wget ftp://ftp.kernel.org/pub/linux/kernel/people/tiwai/snapshot/alsa-driver-snapshot.tar.gz
tar -xvpf alsa-driver-snapshot.tar.gz
cd alsa-driver
sudo ./configure
sudo make
sudo make install-modules
```

The front audio jacks also work now! However, one problem; when I plug headphones in it still plays through the main speakers. Any ideas?

Cheers,

---

### Post by lidex on 2010-04-24
Add the options to alsa-base.conf and reboot then use alsamixer.

---


---
title: "sound stopped since upgrade to 9.1"
date: 2009-11-27
forum: General Help
---

### Post by etzioni on 2009-11-27
I upgraded the ubuntu to 9.1, since then I do not have any sound, and I cannot fix it.

some resuts I have:

aplay --list-devices
aplay: device_list:223: no soundcards found...


yoav@yoav-desktop:~$ alsamixer
alsamixer: function snd_ctl_open failed for default: No such file or directory
                      

can anyone help before my wife force me back to xp??

---

### Post by lloyd_b on 2009-11-27
> **etzioni said:**
> I upgraded the ubuntu to 9.1, since then I do not have any sound, and I cannot fix it.

some resuts I have:

aplay --list-devices
aplay: device_list:223: no soundcards found...


yoav@yoav-desktop:~$ alsamixer
alsamixer: function snd_ctl_open failed for default: No such file or directory
                      

can anyone help before my wife force me back to xp??

Any idea what your sound hardware is?  If not, try running "lspci" and see if it has a device referred to as "multimedia" or "audio".

Without knowing what the hardware is, we really can't give you any advice...

Lloyd B.

---

### Post by etzioni on 2009-11-27
Both

yoav@yoav-desktop:~$ lspci |grep audio
yoav@yoav-desktop:~$ lspci |grep multimedia


Return no results. ant other idea hoe I can tell what my hardware is? everything worked find before the 9.10 update.

---

### Post by lloyd_b on 2009-11-27
> **etzioni said:**
> Both

yoav@yoav-desktop:~$ lspci |grep audio
yoav@yoav-desktop:~$ lspci |grep multimedia


Return no results. ant other idea hoe I can tell what my hardware is? everything worked find before the 9.10 update.

First off, your greps aren't reliable, since you didn't specify case-insensitive (it could be Multimedia, for example).  Could you post the full output of 'lspci' please?  It shouldn't be that long.

You can also run "lshw", and look for a "Multimedia" section.  The full output of this one will be pretty long, so you might want to redirect it to a file.

Lloyd B.

---

### Post by cmptekinc on 2009-11-27
I had a similar issue in 8.04, 8.10 and now 9.10
I couldn't fix the sound in 8.04, I then upgraded to 8.10 and was able to fix the sound problem after following instructions in numerous forums. This morning I upgraded to 9.10 and guess what, surprise, surprise the sound didn't work again....
Anyway, being a long time Windows User and a newbie to LInux, I did what any Sys Admin does, play around, somehow I got the sound to work.
I had to open Alsa Mixer, it has to be running on my system in order for sound to work (Dell Latitude D630)

Below is what my settings are:
System > Pref. > Sound
Sounds and Events: AutoDetect
Music and Movies: AutoDetect
Audio Conferencing>Sound Playback: AutoDetect
Audio Conferencing>Sound Capture: Test Sound

What I think actually fixed the sound issue is opening up Gnome Alsa Mixer (Applications > Sound & Video > Gnome Alsa Mixer)
I muted it and then Unmuted, also maxed everything out (to 100% on Master, PCM, Front)

I should also clarify that originally the sound didn't work only from web on Opera and Firefox both, I was able to play CDs and sound worked fine but not on the web...
This is my 2cents, hopefully you will be able to fix your sound issue.
I didn't have to edit any of the files, so in my case it was all about checking and unchecking the settings as well as starting AlsaMixer.

Also, in System > Pref. > Sound I could only get Test sound when OSS was checked, this was before I opened AlsaMixer, after opening Alsa mixer I changed to AutoDetect and it now works....

---

### Post by etzioni on 2009-11-28
> **lloyd_b said:**
> First off, your greps aren't reliable, since you didn't specify case-insensitive (it could be Multimedia, for example).  Could you post the full output of 'lspci' please?  It shouldn't be that long.
lloyd B.

yoav@yoav-desktop:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx)
00:0a.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 5)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon HD 3200 Graphics
01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
03:0e.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)

no Multimedia either
> **lloyd_b said:**
> 
You can also run "lshw", and look for a "Multimedia" section.  The full output of this one will be pretty long, so you might want to redirect it to a file.
lloyd B.


pasted here: [http://paste.ubuntu.com/330012/](http://paste.ubuntu.com/330012/)

---

### Post by etzioni on 2009-11-28
> **cmptekinc said:**
> I had a similar issue in 8.04, 8.10 and now 9.10
I couldn't fix the sound in 8.04, I then upgraded to 8.10 and was able to fix the sound problem after following instructions in numerous forums. This morning I upgraded to 9.10 and guess what, surprise, surprise the sound didn't work again....
Anyway, being a long time Windows User and a newbie to LInux, I did what any Sys Admin does, play around, somehow I got the sound to work.
I had to open Alsa Mixer, it has to be running on my system in order for sound to work (Dell Latitude D630)

Below is what my settings are:
System > Pref. > Sound
Sounds and Events: AutoDetect
Music and Movies: AutoDetect
Audio Conferencing>Sound Playback: AutoDetect
Audio Conferencing>Sound Capture: Test Sound

What I think actually fixed the sound issue is opening up Gnome Alsa Mixer (Applications > Sound & Video > Gnome Alsa Mixer)
I muted it and then Unmuted, also maxed everything out (to 100% on Master, PCM, Front)

I should also clarify that originally the sound didn't work only from web on Opera and Firefox both, I was able to play CDs and sound worked fine but not on the web...
This is my 2cents, hopefully you will be able to fix your sound issue.
I didn't have to edit any of the files, so in my case it was all about checking and unchecking the settings as well as starting AlsaMixer.

Also, in System > Pref. > Sound I could only get Test sound when OSS was checked, this was before I opened AlsaMixer, after opening Alsa mixer I changed to AutoDetect and it now works....

alsa mixer is not working either

yoav@yoav-desktop:~$ alsamixer
alsamixer: function snd_ctl_open failed for default: No such file or directory

---

### Post by lloyd_b on 2009-11-28
Okay, we've identified your sound hardware:```
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx)
00:0a.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 5)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
**00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)**
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon HD 3200 Graphics
**01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller**
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
03:0e.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
```And a quick search turns up [this thread]("http://ubuntuforums.org/showthread.php?t=1124049"), which seems to be for identical hardware.  See if the idea in post #3 of that thread helps with your system.

Lloyd B.

---

### Post by etzioni on 2009-11-29
> **lloyd_b said:**
> Okay, we've identified your sound hardware:

And a quick search turns up [this thread]("http://ubuntuforums.org/showthread.php?t=1124049"), which seems to be for identical hardware.  See if the idea in post #3 of that thread helps with your system.

Lloyd B.

They suggested to reedit  /etc/modprobe.d/sound , which I do not have, in the libarary I found the following files:

yoav@yoav-desktop:~$ ls ../../etc/modprobe.d/
alsa-base.conf          blacklist-firewire.conf     blacklist-watchdog.conf
alsa-base.conf~         blacklist-framebuffer.conf  libpisock9.conf
blacklist-ath_pci.conf  blacklist-modem.conf
blacklist.conf          blacklist-oss.conf

---

### Post by lloyd_b on 2009-11-29
> **etzioni said:**
> They suggested to reedit  /etc/modprobe.d/sound , which I do not have, in the libarary I found the following files:

yoav@yoav-desktop:~$ ls ../../etc/modprobe.d/
alsa-base.conf          blacklist-firewire.conf     blacklist-watchdog.conf
alsa-base.conf~         blacklist-framebuffer.conf  libpisock9.conf
blacklist-ath_pci.conf  blacklist-modem.conf
blacklist.conf          blacklist-oss.conf

Try *creating* a "/etc/modprobe.d/sound" file, with the contents as specified in that post.  I believe that's all that is required.  Note that you'll need root permissions to do this, so "sudo nano /etc/modprobe.d/sound" or something similar.

Alternately, adding those lines to the end of "/etc/modprobe.d/alsa-base.conf" should work as well.

Lloyd B.

---

### Post by etzioni on 2009-11-30
> **lloyd_b said:**
> Try *creating* a "/etc/modprobe.d/sound" file, with the contents as specified in that post.  I believe that's all that is required.  Note that you'll need root permissions to do this, so "sudo nano /etc/modprobe.d/sound" or something similar.

Alternately, adding those lines to the end of "/etc/modprobe.d/alsa-base.conf" should work as well.

Lloyd B.


I have tried both, separately. none work,

I still get

 yoav@yoav-desktop:~$ alsamixer

alsamixer: function snd_ctl_open failed for default: No such file or directory

---

### Post by lloyd_b on 2009-11-30
> **etzioni said:**
> I have tried both, separately. none work,

I still get

 yoav@yoav-desktop:~$ alsamixer

alsamixer: function snd_ctl_open failed for default: No such file or directory

What does "aplay -l" give you?  Is it showing your sound hardware at all?

Lloyd B.

---

### Post by dreadood on 2009-11-30
If none of these things work you can also give OSS4 a try, worked with me in ubuntu 9.04 on my laptop. Sound finally worked out of the box through a fresh install of ubuntu 9.10.


Follow the preparation part of the following guide:
[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

Download the right deb package (x86 or amd64) from here:
[http://www.opensound.com/download.cgi](http://www.opensound.com/download.cgi)

and install it.

That did the trick for me when I had no sound.

dreadood

---

### Post by etzioni on 2009-12-01
> **lloyd_b said:**
> What does "aplay -l" give you?  Is it showing your sound hardware at all?

Lloyd B.
yoav@yoav-desktop:~$ aplay -l
aplay: device_list:223: no soundcards found...

---

### Post by lloyd_b on 2009-12-02
> **etzioni said:**
> yoav@yoav-desktop:~$ aplay -l
aplay: device_list:223: no soundcards found...

I'm out of ideas, so I'd suggest doing a search and reading through the various posts.  There seems to be a lot of issues involving the Intel HDA audio, but I can't tell for sure which ones actually apply to your system.

[Here's one]("http://ubuntuforums.org/showthread.php?t=1316634") that looks like it has some useful suggestions.

Lloyd B.

---

### Post by john newbuntu on 2009-12-02
Make sure you are in the right group.
system->administration->users and groups->click to make changes.
enter password.
Then choose manage groups. Select "plugdev" and click properties. Make sure your userid is checked and click OK.

---

### Post by lloyd_b on 2009-12-02
Just a screwy idea to try - in a terminal window```
sudo aplay -l
```.  I had problems with my system after upgrading to 9.10 that turned out to be a result of the existing config files conflicting with something.

Net result - I could access aplay/alsamixer via the sudo, but when I tried it without I got that same error.

Just a shot in the dark...

Lloyd B.

---

### Post by etzioni on 2009-12-05
> **lloyd_b said:**
> I'm out of ideas, so I'd suggest doing a search and reading through the various posts.  There seems to be a lot of issues involving the Intel HDA audio, but I can't tell for sure which ones actually apply to your system.

[Here's one]("http://ubuntuforums.org/showthread.php?t=1316634") that looks like it has some useful suggestions.

Lloyd B.

None of the suggestion seems to fit. However I found that when loading a ubunto from live cd the sound work just fine. So if anyone has idea what else I should check, I love to here it, if not I'll simply format and reintnstall.

---


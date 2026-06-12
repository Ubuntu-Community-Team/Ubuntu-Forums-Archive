---
title: "Sound works sometimes (plus a bug when it doesn't work)"
date: 2010-07-06
forum: General Help
---

### Post by Maximo7274 on 2010-07-06
I just got Ubuntu 10.04 and everything seemed to work fine. After a couple of days, I booted it up and the sound icon showed that the sound was off.

This seemed weird as my speakers were on, and I clicked on it and it didn't even recognize that my speakers were plugged in.  I tried plugging and replugging but nothing happened.

I decided to just try and reboot, and I clicked restart. It bumped me back to the sign in page.  I tried everything to shut my computer down normally (shut-down, shut-down from sign-in page, etc.) and I ended up having to force shutdown.

Now i have this problem at random times.  Sometimes everything works, sometimes it doesn't.

If anyone can help me in any way it would be greatly appreciated.

---

### Post by lidex on 2010-07-07
Can you post the output of these terminal commands for me please:
```
uname -a
aplay -l
dpkg -l | grep "alsa"
head -n 1 /proc/asound/card*/codec#* 
```
Terminal="Applications->Accessories->Terminal"
**Please also include the make/model of your PC/Laptop.**
Please post text output using code tags (the # in toolbar)

---

### Post by Maximo7274 on 2010-07-07
Okay. This is what I got:
```

byron@byron-desktop:~$ uname -a
Linux byron-desktop 2.6.32-23-generic #37-Ubuntu SMP Fri Jun 11 07:54:58 UTC 2010 i686 GNU/Linux
byron@byron-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
byron@byron-desktop:~$ dpkg -l | grep "alsa"
ii  alsa-base                            1.0.22.1+dfsg-0ubuntu3                          ALSA driver configuration files
ii  alsa-utils                           1.0.22-0ubuntu5                                 ALSA utilities
ii  bluez-alsa                           4.60-0ubuntu8                                   Bluetooth audio support
ii  gstreamer0.10-alsa                   0.10.28-1                                       GStreamer plugin for ALSA
byron@byron-desktop:~$ head -n 1 /proc/asound/card*/codec#*
Codec: Realtek ALC1200
byron@byron-desktop:~$ 

```
The model of my computer is HP Pavilion Slimline s3200z

---

### Post by lidex on 2010-07-07
No guarantees, but you can try this. Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert these lines at the bottom:
```
options snd slots=snd-hda-intel
alias snd-card-0 snd-hda-intel
options snd-hda-intel probe_mask=1
```
Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab.

---

### Post by Maximo7274 on 2010-07-11
Thanks, i haven't had any problems after I edited the file, so I think it worked.

---

### Post by lidex on 2010-07-11
Great. Wasn't sure about that one. :-k
When you feel confident the issue is fixed, would you mind marking the thread solved via 'Thread Tools' up top? Thanks!

---


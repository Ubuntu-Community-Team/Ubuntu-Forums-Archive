---
title: "ALSA 1.0.23 - Still no HDMI device"
date: 2010-08-07
forum: General Help
---

### Post by bprins on 2010-08-07
Hi,

I'm a bit confused. I am still struggling with getting my HDMI working under Ubuntu lucid. 

I added the ricotz/unstable repositories to get the latest version of ALSA (1.0.23):
```

sudo add-apt-repository ppa:ricotz/unstable
sudo apt-get update 
sudo apt-get upgrade
```
All 1.0.23 related packages were installed (Alsa base, alsa utils, libasound).

If I check the ALSA version in /proc/asound:
```

bas@ubuntu-lt:~$ cat /proc/asound/version 
Advanced Linux Sound Architecture Driver Version 1.0.21.
``` 

Result, still no HDMI ports available when I type aplay -l:
```

bas@ubuntu-lt:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC272 Analog [ALC272 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
```

I got this working under Karmic. What am I doing wrong?

Help is appreciated! Thanks in advance.

Bas

---

### Post by bprins on 2010-08-07
Further more:
```

alsamixer -c 1:

Card: HDA NVidia
Chip: Nvidia ID a
&#9474;  This sound device does not have any controls.          

```

---

### Post by speedwell68 on 2010-08-07
I'll watch this one with interest as I am having the exact same problems.

---

### Post by dino99 on 2010-08-07
follow this link:

[http://alsa.opensrc.org/index.php/DigitalOut](http://alsa.opensrc.org/index.php/DigitalOut)

---

### Post by speedwell68 on 2010-08-07
> **dino99 said:**
> follow this link:

[http://alsa.opensrc.org/index.php/DigitalOut](http://alsa.opensrc.org/index.php/DigitalOut)

Looks useful, thanks.

---

### Post by bprins on 2010-08-07
Hi,

Thanks for the pointer. 

The thing is, for some reason my nvidia sound card is not listed in aplay. 

```

bas@ubuntu-lt:~$ cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xb7100000 irq 22
 1 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xb3000000 irq 16

``` 
```

bas@ubuntu-lt:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC272 Analog [ALC272 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

``` 

I had the same problem on Karmic, there it was solved with Alsa 1.0.23. So I've updated with the packages from rizotz/unstable, but cat /proc/asound/version still gives 1.0.21 (while synaptic does tell me that alsa-base 1.0.23 is installed).

So my guess is that it goes wrong at some point there.

Any clue?

thanks in advance.

Bas

---

### Post by bprins on 2010-08-07
Problem solved. 

I found a post where they solved it by upgrading the alsa kernel driver. 

If anybody has the same issue, this is what you need to do to solve the problem:

1) Add the repository for audio packages:
```

add-apt-repository ppa:ubuntu-audio-dev/ppa

```

2) Check your kernel version:
```

uname -a

```

For me this is:
```

bas@ubuntu-lt:~$ uname -a
Linux ubuntu-lt **2.6.32-24-generic** #39-Ubuntu

```

3) The install the alsa kernel driver:
```

sudo apt-get install linux-alsa-driver-modules-**2.6.32-24-generic**

```
Note: the bold part should be replaced by your own kernel version (uname -a)

4) Reboot and check ur aplay -l output
```

bas@ubuntu-lt:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC272X Analog [ALC272X Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

Good luck.

Bas

---

### Post by bprins on 2010-08-07
Once you have your HDMI devices, do not forget to unmute them in alsamixer.

```

alsamixer -c 1

```

Note the -c 1. That tells alsamixer which card you want to tune. Unmute a device with the 'm' key.

---

### Post by kellymartinv on 2010-09-02
Had the same problem and installing that fixed it up for me, thanks!

---

### Post by IndieRockSteve on 2010-09-15
**bprins** directions worked perfectly for me on two systems. thanks!

---

### Post by Diego318 on 2010-09-23
E: Couldn't find package linux-alsa-driver-modules-2.6.32-24-generic



:confused:

---

### Post by bprins on 2010-09-24
A lot is changing for alsa and pulse in the process to 10.10 (maverick).

I think the package is backported already.

Do you have problems with HDMI?

The package might be available as backport:

```

bas@ubuntu-laptop:~$ apt-cache search alsa-driver
linux-backports-modules-alsa-lucid-generic - Backported drivers for alsa-driver snapshot.

```

Keep your eyes open for 10.10. I installed maverick on a different partition and everything works without tweaking. Maverick is beta now, and works like a charm here.

---

### Post by bwallum on 2010-11-14
I'm running Maverick i386 and using a nVidia gpu Asus EH210 graphics card with HDMI output. It's going to a Samsung HD TV with two HDMI inputs. 

Video is very good, sound is dead.

Does anybody have an update on how to get sound working in Maverick? I have read (and tried) various thread solutions but I understand from this thread that significant changes have been made to ALSA and PulseAudio in the Maverick release, hence this enquiry.

EDIT
Very simple, as ever when you know the answer. The trick (in Maverick) is to find the right sound device and unmute it. The sound hardware in my case was designated '0' (zero) for my motherboard sound and '1' for my nVidia card HDMI sound. To unmute I ran```
alsamixer -c 1
``` The '-c 1' means that alsamixer loads the settings for my HDMI sound. Then unmute by pressing the 'm' key where it shows as MM.

Thanks to all the above contributions for pointing me in the right direction.

---

### Post by sydbat on 2010-11-18
Got everything installed, as per this thread, and no sound. The nVidia HD audio shows up and I have unmuted all. Still nothing. 

Is there some other step that I may have missed (I read and followed this entire thread) or some step that was accidentally excluded from this thread?

Do I have to disable my on-board sound card in BIOS for this to work?

I'd really like to have sound through my HDMI connection, but nothing to this point has worked.

---


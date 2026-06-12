---
title: "random freezes lucid lynx 10.04"
date: 2011-10-27
forum: General Help
---

### Post by tredsyn on 2011-10-27
I'm getting random freezes for short periods (from 4 secs - 20 secs). Using 3 browsers at the same time, sometimes 1 of the browsers will freeze, but the other 2 would still work. Sometimes 3 of the browsers work, but the audio in the musicplayer will be interrupted. Sometimes the mouse cursor will stop moving, freeze for a few seconds, with audio or video playing. I tried to run musicplayer(without any other applications open) but still get the problem. Audio will be muted for a few seconds, but the player would still show that it is still playing. Same thing happens for videos. These things happen 1 at a time, or combination of 2 or all at the same time. Same thing happens on any program/applications.

System: 
dual boot: windows xp sp2/ (tango studio based on) ubuntu lucid 10.04
Processor: Intel Pentium M processor 1.60 GHz
kernel linux 2.6.32-34-lowlatency
memory: 970.8 MiB
swap: 1.9 GiB
GNOME 2.30.2
video card: VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
Using ethernet connection; wireless card always disabled(not used)
took out batteries, running on AC power
compiz not installed
metacity's compositing feature disabled

Troubleshooting thus far: (I did the troubleshooting in this order, with the necessary reboot of some steps)
1. Reinstalled OS(not really sure if i reinstalled 3 or 4 times already).
2. Replicate problem on Windows XP: no problem on xp
3. Used 3 different browsers(chrome, chromium, firefox); used 3 different players (exaile, banshee, gnome player). 
4. Tried using 1 browser only.
5. Tried using musicplayer only (no other programs open)
6. Took out usb mouse; used only touchpad.
7. Disable GL screensaver.
8. Disable screensaver.
9. Install updates.
10. Update/replaced kernel (now using 2.6.32-34-lowlatency)
11. Run memtest: passed

the only thing I noticed based on the logs everytime it freezes

> Oct 27 20:20:19 kernel: [ 3712.985478] ata1.00: configured for UDMA/100
Oct 27 20:20:19 kernel: [ 3713.026460] ata1.01: configured for PIO0
Oct 27 20:20:19 kernel: [ 3713.029736] ata1: EH complete

I just started using linux a few weeks ago. I'm very familiar with windows tweaking, but on linux I'm a comlete noob  
I've been lurking the forums for a couple of weeks now but havent got info on how to fix this yet
any suggestions?
BTW if this post is exactly similar to any previous thread, kindly post a link to it.

---

### Post by searchfgold6789 on 2011-10-27
Try seeing if your computer is set to check for updates in intervals of time. Even on my P4 that lags the computer severely, so I put it to once a day.
You may try seeing if the same behavior occurs while using a Live CD or a different version of Ubuntu - the latest one is 11.10 which is what most people are using, and you wouldn't be using unity because of your hardware. LTS is typically used by those looking for a fallback for hardware compatibility purposes. You could try 11.04 too.
If nothing else works, try running "top" from a terminal.
That's all I got. Hopefully someone more advanced in this topic will stop by. :D

---

### Post by tredsyn on 2011-10-27
Thanks for the reply,

I got mine to "check for updates: weekly"
Should I change it to "daily" or leave it as it is?

I currently have ubuntu 11.10 on LiveUSB (which I dislike; I was staring at my monitor looking for buttons  ](*,) not really familiar with the new Unity). I'd be downloading ubuntu 11.04 iso (demoed it before from a LiveUSB but didn't notice any problem). For the meantime I'm gonna monitor my system using "top" just like you suggest.

---

### Post by tredsyn on 2011-10-28
Monitoring my system using "top", the only things noticeable are the obvious ones: browsers, gnome, and xorg, but the peaks doesn't coincide with the freeze.

I'm currently booted to Ubuntu 11.04 LiveUSB to check if I'd be getting the same problem.

Any other suggestions on what I could check on?

---

### Post by searchfgold6789 on 2011-10-28
Running from the Live USB, your system is going to be a lot slower than if you were running from a hard disk, and as browsers make requests for data from the thumb drive, the program will most certainly freeze until it gets the data it needs. Unfortunately,USB thumb drives have much slower data transfer rates than hard disks do.
Therefore, your problem is not a matter of computer resources or software faults, but with the data transfer speed of the installation medium. If you desire better software behavior, migrate to a hard disk.
 - search

---

### Post by tredsyn on 2011-10-29
hey thanks for the reply.

I tried running from LiveUSB, 2 browsers open, 1 tab each playing non-heavy flash browser game + playing an mp4 on movie player. Froze within 10 minutes, except that the  mouse cursor is still moving. I have to power off/reboot a couple of times. 

Note that previously I was able to run natty 11.04 from live USB with 2 browsers, 4 tabs each doing internet surfing, watching/loading youtube videos, playing (heavy & non-heavy) flash games all at the same time but did not encounter severe lag (now taking a minute or more considering I'm running from USB) or a complete freeze :confused:

I'll be switching to Xfce DE from Gnome though I doubt it will solve my problem. If there's still that annoying interruption/freeze I'll just have to install something else *sigh* Maybe Ubuntu Studio (with realtime kernel & XFCE)

---

### Post by searchfgold6789 on 2011-10-29
I don't know much about how the Live USB handles RAM, but you may try creating a swap partition.

---

### Post by tredsyn on 2011-10-31
Got a fresh Xubuntu 11.04 install. Everything is now working a bit faster especially the file manager. And I'm now getting a different and more tolerable problem.

PC only freezes if [Flash is used + CPU load is too high] but this time it's a complete freeze (mouse cursor moving but nothing on the screen I could click on) which would require me to reboot PC. Upon further reading (and lurking), I think there's a problem on the BIOS (because of weak cmos battery) or maybe the drive (pATA).

So far it's working fine as long as I avoid opening anything that uses flash in google chrome, avoiding any flash content in chromium. I installed flash-aid in firefox which I'm using for youtube videos.

As far as my original problem goes, it's lost in the twilight zone...

---


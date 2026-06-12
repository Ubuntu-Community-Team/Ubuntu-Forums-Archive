---
title: "VMWare Workstation 7.1.2 build-301548 increased CPU on vmware-vmx, pulseaudio choppy"
date: 2010-10-16
forum: General Help
---

### Post by Kalidarn on 2010-10-16
Hi,

I'm running Kubuntu 10.10, with KDE 4.5.1, what I've noticed is every after a while (while running my windows VM) the CPU usage on vmware-vmx seems to jump up to 50-100% and my audio goes all choppy.

I was watching a video in VLC on my host and doing code in a windows 7 vm running visual studio (in the vm), and then all of a sudden I noticed my whole machine went all laggy and choppy.

The only way I've found to fix this is to shut down the virtual machine, and restart the pulse audio service.

It seems doing one or the other doesn't fix the problem. I'm not sure if this is directly related to running KDE vs using Gnome but I guess it's possible that 10.10 introduced this bug after all I found I needed to use this patch [http://www.sputnick-area.net/scripts/vmware7.1.1-patch-kernel-2.6.35.bash](http://www.sputnick-area.net/scripts/vmware7.1.1-patch-kernel-2.6.35.bash)
 to even get it to run.

Could it possibly be related to [http://communities.vmware.com/message/711580](http://communities.vmware.com/message/711580) that seems very old though.

Edit: I meant to say KDE 4.5.1.

---

### Post by dcstar on 2010-10-16
> **Kalidarn said:**
> Hi,

I'm running Kubuntu 10.10, with KDE 4.5.2, what I've noticed is every after a while (while running my windows VM) the CPU usage on vmware-vmx seems to jump up to 50-100% and my audio goes all choppy.
......

VM issues should be in the Virtualization forum.

---

### Post by Kalidarn on 2010-10-17
I've renamed this thread as it's clearly not a VMWare issue any more.

I was using VLC, Amarok, Firefox, Netbeans and Thunderbird, then all of a sudden my system started lagging heaps and the video I was watching in VLC all laggy and unmatchable, sounds in pidgin sounded delayed too.

Here's the output of top, while running a video with a few other things. 

```

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 2180 user  20   0  942m 177m  81m S   20  3.0  55:50.22 kwin
 1559 root      20   0  704m 602m  79m S    6 10.1  21:49.63 Xorg
 2306 user  20   0  411m  32m  16m S    3  0.5   0:51.44 yakuake
 2291 user   9 -11  351m  15m  13m S    2  0.3   1:03.20 pulseaudio
 4630 user  20   0  861m 123m  83m S    1  2.1  15:52.54 vlc
 1982 user  20   0 26036 2692  692 S    0  0.0   0:06.90 dbus-daemon
 2288 user  20   0  657m  40m  20m S    0  0.7   0:08.78 krunner
 2564 user  20   0 1083m 245m  32m S    0  4.1  10:13.48 firefox-bin
 4985 user  20   0 1229m 449m  31m S    0  7.5   0:32.29 java
 5038 user  20   0 76684  14m 9708 S    0  0.2   0:01.17 npviewer.bin
    1 root      20   0 23892 2012 1232 S    0  0.0   0:01.73 init
    2 root      20   0     0    0    0 S    0  0.0   0:00.00 kthreadd
    3 root      20   0     0    0    0 S    0  0.0   0:00.59 ksoftirqd/0

```

And when I left VLC play again this happens:

```

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 4630 user  20   0  861m 123m  83m S   35  2.1  15:58.01 vlc
 2180 user  20   0  942m 177m  81m R   30  3.0  56:21.28 kwin
 1559 root      20   0  704m 602m  79m S    6 10.1  21:57.82 Xorg
 2306 user  20   0  411m  32m  16m S    2  0.5   0:53.07 yakuake
  540 root      20   0     0    0    0 S    1  0.0   1:29.13 kcryptd
  110 root      20   0     0    0    0 S    0  0.0   0:03.48 kondemand/1
 2058 root      20   0 24544 1180  980 S    0  0.0   0:01.23 hald-addon-stor
 2288 user  20   0  657m  40m  20m S    0  0.7   0:08.80 krunner
 2291 user   9 -11  351m  15m  13m S    0  0.3   1:05.99 pulseaudio
 4985 user  20   0 1229m 449m  31m S    0  7.5   0:32.79 java
 5140 user  20   0 19408 1476  972 R    0  0.0   0:00.66 top
    1 root      20   0 23892 2012 1232 S    0  0.0   0:01.73 init
    2 root      20   0     0    0    0 S    0  0.0   0:00.00 kthreadd
    3 root      20   0     0    0    0 S    0  0.0   0:00.59 ksoftirqd/0

```
CPU usage and memory usage spike.

I see a whole heap of in /var/log/messages

```

Oct 17 21:00:13 kothas pulseaudio[2291]: ratelimit.c: 13 events suppressed
Oct 17 21:00:18 kothas pulseaudio[2291]: ratelimit.c: 14 events suppressed
Oct 17 21:00:24 kothas pulseaudio[2291]: ratelimit.c: 8 events suppressed
Oct 17 21:00:29 kothas pulseaudio[2291]: ratelimit.c: 24 events suppressed
Oct 17 21:00:34 kothas pulseaudio[2291]: ratelimit.c: 9 events suppressed
Oct 17 21:00:39 kothas pulseaudio[2291]: ratelimit.c: 7 events suppressed
Oct 17 21:00:45 kothas pulseaudio[2291]: ratelimit.c: 5 events suppressed
Oct 17 21:00:50 kothas pulseaudio[2291]: ratelimit.c: 16 events suppressed
Oct 17 21:00:55 kothas pulseaudio[2291]: ratelimit.c: 4 events suppressed
Oct 17 21:01:00 kothas pulseaudio[2291]: ratelimit.c: 2 events suppressed
Oct 17 21:01:06 kothas pulseaudio[2291]: ratelimit.c: 10 events suppressed

```

I never experienced this on Gnome, however that was 10.04 so I cannot be sure 10.10 somehow didn't break something with pulseaudio.

I've now killed pulseaudio with "pulseaudio -k"

```

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 2180 user  20   0  938m 173m  77m S   26  2.9  57:48.61 kwin
 1559 root      20   0  704m 602m  79m S    6 10.1  22:19.69 Xorg
 2306 user  20   0  411m  32m  16m S    5  0.5   0:56.43 yakuake         
 2293 rtkit     21   1 43704 1308 1068 S    0  0.0   0:00.12 rtkit-daemon
 2564 user  20   0 1083m 245m  32m S    0  4.1  10:14.94 firefox-bin
 4985 user  20   0 1229m 449m  31m S    0  7.5   0:33.76 java
 5329 user  20   0 19408 1480  972 R    0  0.0   0:00.06 top
    1 root      20   0 23892 2012 1232 S    0  0.0   0:01.73 init
    2 root      20   0     0    0    0 S    0  0.0   0:00.00 kthreadd
    3 root      20   0     0    0    0 S    0  0.0   0:00.61 ksoftirqd/0
    4 root      RT   0     0    0    0 S    0  0.0   0:00.13 migration/0

```
I decided to try playing the video in VLC again:

```

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 4630 user  20   0  861m 137m  83m S   50  2.3  16:32.85 vlc
 2180 user  20   0  938m 173m  77m S   30  2.9  58:01.58 kwin
 1559 root      20   0  704m 602m  79m S    7 10.1  22:23.49 Xorg
  540 root      20   0     0    0    0 S    3  0.0   1:31.06 kcryptd
 2306 user  20   0  411m  32m  16m S    2  0.5   0:56.89 yakuake
 2564 user  20   0 1083m 245m  32m S    0  4.1  10:15.23 firefox-bin
 4985 user  20   0 1229m 449m  31m S    0  7.5   0:33.90 java 
 5038 user  20   0 76684  14m 9708 S    0  0.2   0:02.09 npviewer.bin
 5329 user  20   0 19408 1480  972 R    0  0.0   0:00.22 top
    1 root      20   0 23892 2012 1232 S    0  0.0   0:01.73 init

```
Still seeing laggy cpu usage, obviously now without sound.

I'll restart pulseaudio again with "pulseaudio -D --log-target=syslog"

```

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 5372 user  20   0  858m 117m  83m S   61  2.0   1:05.13 vlc
 2180 user  20   0  930m 165m  69m S   27  2.8  59:12.33 kwin
 1559 root      20   0  704m 602m  78m S    9 10.1  22:48.96 Xorg
 2306 user  20   0  411m  32m  16m S    3  0.5   1:06.36 yakuake
 5309 user   9 -11  340m 8288 6556 S    1  0.1   0:02.49 pulseaudio
 5485 user  20   0 19408 1488  972 R    1  0.0   0:00.05 top
  113 root      20   0     0    0    0 S    0  0.0   0:03.28 kondemand/4
 2564 user  20   0 1083m 245m  32m S    0  4.1  10:16.11 firefox-bin
 4985 user  20   0 1229m 449m  31m S    0  7.5   0:34.86 java
    1 root      20   0 23892 2012 1232 S    0  0.0   0:01.73 init
    2 root      20   0     0    0    0 S    0  0.0   0:00.00 kthreadd
    3 root      20   0     0    0    0 S    0  0.0   0:00.62 ksoftirqd/0
    4 root      RT   0     0    0    0 S    0  0.0   0:00.13 migration/0
    5 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/0
    6 root      RT   0     0    0    0 S    0  0.0   0:00.07 migration/1

```
Still seeing high CPU usage, but the video isn't choppy any more. Also the same thing happens in Dragon Player so it's not a VLC bug.

There doesn't seem to be any more of those ratelimit.c: XXX events suppressed any more.

After reboot

```

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 2913 user  20   0  858m 121m  83m S   44  2.0   0:17.07 vlc
 2178 user  20   0  712m  98m  66m S   29  1.7   0:48.65 kwin
 1437 root      20   0  209m 110m  82m S    9  1.8   0:27.50 Xorg
 2297 user  20   0  415m  37m  17m S    2  0.6   0:02.68 yakuake
  546 root      20   0     0    0    0 S    2  0.0   0:09.79 kcryptd
 2283 user   9 -11  351m 9.8m 8080 S    1  0.2   0:00.83 pulseaudio
 2374 user  20   0  683m 191m  30m S    1  3.2   0:13.90 firefox-bin
 2848 user  20   0 1248m 506m  30m S    0  8.5   0:36.01 java
 2959 user  20   0 19408 1500  972 R    0  0.0   0:00.11 top
    1 root      20   0 23888 2100 1316 S    0  0.0   0:01.72 init
    2 root      20   0     0    0    0 S    0  0.0   0:00.00 kthreadd
    3 root      20   0     0    0    0 S    0  0.0   0:00.02 ksoftirqd/0
    4 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/0
    5 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/0
    6 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/1

```

I'm not quite sure if that CPU usage is normal for vlc and kwin, seems a bit high to me.

---

### Post by Kalidarn on 2010-10-27
The problem here would appear to be PulseAudio.

> Glitches and high CPU usage since 0.9.14

The PulseAudio sound server has been rewritten to use timer-based audio scheduling instead of the traditional interrupt-driven approach. Timer-based scheduling may expose issues in some Alsa drivers. To turn timer-based scheduling off, replace the line:

```
load-module module-udev-detect 
```

in /etc/pulse/default.pa by:

```
load-module module-udev-detect tsched=0
```

Choppy sound

Choppy sound in pulsaudio can result from wrong settings for the sample rate in /etc/pulse/daemon.conf. Try changing the line

```
; default-sample-rate = 44100
```

to

```
default-sample-rate = 48000
```

and restart the pulsaudio server by executing

```
pulseaudio --kill && pulseaudio --start
```

[http://wiki.archlinux.org/index.php/PulseAudio#Choppy_sound](http://wiki.archlinux.org/index.php/PulseAudio#Choppy_sound)

This hasn't seemed to help fix it, I've considered switching to OSS4 but then I'm not sure if the Quickcam 9000 microphone will work as I've heard USB microphones can be a problem with OSS. It's a pity sound in Linux is in such a sad state when compared with say OSX.

---

### Post by Kalidarn on 2010-10-31
It could have possibly been the NVIDIA proprietary drivers and the "Blur" compositing effect causing high cpu usage it's known to have problems, ever since I disabled it everything has settled down, even when the VM was shut.

---

### Post by Kalidarn on 2010-11-20
Turns out I think it's much more likely to this bug: [https://bugs.launchpad.net/bugs/665796](https://bugs.launchpad.net/bugs/665796) Intel Core i7, nVidia proprietary - Timer interrupt freezes, system becomes sluggish

Same combination of hardware as me and exactly the same symptoms on exactly the same configuration.

---


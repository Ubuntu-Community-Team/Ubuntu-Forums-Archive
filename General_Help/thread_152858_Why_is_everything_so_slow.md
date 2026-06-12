---
title: "Why is everything so slow?"
date: 2006-03-30
forum: General Help
---

### Post by melissathespud on 2006-03-30
I cannot multi task on this computer running linux, as everything goes entirely too slow.  The main problem is when I try to play java-based games online.  Some of the speed-based ones are just too slow to play, even with nothing open but firefox and gaim.  If I try to play even card games they run slowly, moreso if I have gmail open (or anything that auto-refreshes) and unbearably so if I should (heaven forbid) attempt to run xine or a music player to play my music.  Let me first say that it is *not* the computer itself.  All of these programs ran just fine when I had windows installed on this very same computer.  

Any thoughts?  Suggestions?  Etc?

---

### Post by henriquemaia on 2006-03-30
[QUOTE=melissathespud]I cannot multi task on this computer running linux, as everything goes entirely too slow.  The main problem is when I try to play java-based games online.  Some of the speed-based ones are just too slow to play, even with nothing open but firefox and gaim.  If I try to play even card games they run slowly, moreso if I have gmail open (or anything that auto-refreshes) and unbearably so if I should (heaven forbid) attempt to run xine or a music player to play my music.  Let me first say that it is *not* the computer itself.  All of these programs ran just fine when I had windows installed on this very same computer.  

Any thoughts?  Suggestions?  Etc?[/QUOTE]

I was having the same problem today. Everything was painfully slow. Then I did an update using apt-get and now all runs normal again. Probably not the same problem as you, but at least you can try something like that.

---

### Post by melissathespud on 2006-03-30
I don't think it has ever run up to speed, though.  And I install every new update that I am alerted about.  :-/

---

### Post by towsonu2003 on 2006-03-30
I have the same problem as well. On a 2.8Ghz intel celeron with 2GB swap and 1GB memory... I have been having this for about a couple of months now. Tried the following but didn't fix:

1. install proprietary ati drivers (done, no change, reverted back to ati)
2. use radeon instead of ati (fps goes up, no change in speed)
3. install sun's java (no change)

4. Try other browsers (NOT firefox 1.0.7 or 1.5.0.1) => this one works a little bit. I sometimes use Epiphany when I get real pissed off (sudo apt-get install epiphany-browser). 

And here are the ones I didn't do yet:
5. Try a new distro (waiting for ubuntu 6.06 and opensuse 10.1 and finish my thesis)

Above was just to give you some new ideas to speed things up... 

Now for the possible causes:
Please post the output of the following commands (from a terminal)while you are using both gaim, firefox, and whatever AND experiencing the slowdown... 
```

df -h
free -m
top -b -n 1

```

What's your cpu? 

If you are using Firefox 1.0.7 (comes in with Ubuntu), try to install and use Firefox 1.5 (see howto at [https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion) ). Ubuntu's firefox is famous for its slowness... 

Try installing sun's java (as a .deb package, search the forum for that).

Check out available drivers for your video card.

---

### Post by melissathespud on 2006-03-30
df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/mapper/Ubuntu-root
                       37G  3.2G   32G  10% /
tmpfs                 189M     0  189M   0% /dev/shm
tmpfs                 189M   13M  176M   7% /lib/modules/2.6.12-10-386/volatile
/dev/hda1             228M   19M  197M   9% /boot


free -m
             total       used       free     shared    buffers     cached
Mem:           376        371          5          0          7         72
-/+ buffers/cache:        290         85
Swap:         1123         16       1107

 top -b -n 1
top - 19:35:29 up 19:19,  3 users,  load average: 0.90, 0.70, 0.62
Tasks:  90 total,   1 running,  89 sleeping,   0 stopped,   0 zombie
Cpu(s): 20.0% us,  0.6% sy,  0.0% ni, 79.0% id,  0.3% wa,  0.0% hi,  0.0% si
Mem:    385304k total,   380332k used,     4972k free,     7832k buffers
Swap:  1150968k total,    17256k used,  1133712k free,    74684k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
15942 spudgirl  16   0  255m  73m  14m S  3.9 19.7   8:21.64 java_vm
    1 root      16   0  1560  524  456 S  0.0  0.1   0:01.60 init
    2 root      34  19     0    0    0 S  0.0  0.0   0:00.17 ksoftirqd/0
    3 root      10  -5     0    0    0 S  0.0  0.0   0:00.47 events/0
    4 root      10  -5     0    0    0 S  0.0  0.0   0:00.02 khelper
    5 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthread
    7 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid
   71 root      10  -5     0    0    0 S  0.0  0.0   0:00.16 kblockd/0
   99 root      15   0     0    0    0 S  0.0  0.0   0:00.04 pdflush
  100 root      15   0     0    0    0 S  0.0  0.0   0:00.16 pdflush
  102 root      16  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0
  101 root      15   0     0    0    0 S  0.0  0.0   0:00.70 kswapd0
  687 root      15   0     0    0    0 S  0.0  0.0   0:00.00 kseriod
 2260 root      15   0     0    0    0 S  0.0  0.0   0:00.02 khubd
 3734 root      15   0     0    0    0 S  0.0  0.0   0:01.74 kjournald
 3869 root      12  -4  1660  572  480 S  0.0  0.1   0:00.35 udevd
 5458 root      15   0     0    0    0 S  0.0  0.0   0:00.00 kjournald
 5711 root      25   0     0    0    0 S  0.0  0.0   0:00.00 shpchpd_event
 6436 root      25   0     0    0    0 S  0.0  0.0   0:00.00 kgameportd
 6758 dhcp      14  -2  2316 1024  736 S  0.0  0.3   0:00.00 dhclient3
 7102 root      16   0  1816 1012  548 S  0.0  0.3   0:00.00 acpid
 7134 root      16   0  1556  392  324 S  0.0  0.1   0:00.02 dd
 7136 klog      16   0  2456 1564  468 S  0.0  0.4   0:00.14 klogd
 7149 messageb  15   0  2152 1080  908 S  0.0  0.3   0:00.77 dbus-daemon
 7162 hal       16   0  5088 3768 1588 S  0.0  1.0   0:00.89 hald
 7167 hal       18   0  1860  592  504 S  0.0  0.2   0:00.00 hald-addon-acpi
 7176 hal       16   0  1868  632  540 S  0.0  0.2   0:03.71 hald-addon-stor
 7178 hal       16   0  1864  632  540 S  0.0  0.2   0:03.41 hald-addon-stor
 7569 root      16   0 10628 2344 2016 S  0.0  0.6   0:00.00 gdm
 7572 root      16   0 10960 2808 2396 S  0.0  0.7   0:00.34 gdm
 7678 hplip     16   0 20812 1244 1076 S  0.0  0.3   0:00.00 hpiod
 7700 hplip     16   0  8852 5520 2268 S  0.0  1.4   0:00.86 python
 7884 root      16   0  5500 1780 1360 S  0.0  0.5   0:00.33 nmbd
 7886 root      15   0  7760 2352 1824 S  0.0  0.6   0:00.00 smbd
 7902 ntp       16   0  3320 3320 2640 S  0.0  0.9   0:00.77 ntpd
 7915 root      18   0  7760 2324 1808 S  0.0  0.6   0:00.00 smbd
 7916 root      18   0  1916  792  692 S  0.0  0.2   0:00.00 hcid
 7922 root      19   0  1600  528  460 S  0.0  0.1   0:00.00 sdpd
 7932 root      10 -10     0    0    0 S  0.0  0.0   0:00.00 krfcommd
 7956 root      16   0  3320 3320 2640 S  0.0  0.9   0:00.00 ntpd
 7965 daemon    16   0  1760  664  560 S  0.0  0.2   0:00.00 atd
 7978 root      16   0  1824  868  712 S  0.0  0.2   0:00.02 cron
 8030 root      17   0  2280 1088  836 S  0.0  0.3   0:00.01 login
 8031 root      16   0  1552  488  420 S  0.0  0.1   0:00.00 getty
 8032 root      16   0  1552  488  420 S  0.0  0.1   0:00.00 getty
 8033 root      16   0  1556  492  420 S  0.0  0.1   0:00.00 getty
 8034 root      16   0  1552  488  420 S  0.0  0.1   0:00.00 getty
 8035 root      16   0  1552  488  420 S  0.0  0.1   0:00.00 getty
 8174 cupsys    25  10  6312 3316 1200 S  0.0  0.9   0:05.10 cupsd
 8268 syslog    26  10  1772  804  664 S  0.0  0.2   0:00.05 syslogd
 8369 spudgirl  15   0  6664 5248 1220 S  0.0  1.4   0:08.58 esd
11761 spudgirl  16   0  4680 2064 1284 S  0.0  0.5   0:00.03 bash
11773 spudgirl  22   0  4316 1608 1036 S  0.0  0.4   0:00.01 startx
11789 spudgirl  16   0  2360  680  568 S  0.0  0.2   0:00.00 xinit
11790 root      15   0  140m  62m  12m S  0.0 16.7 141:42.42 Xorg
11796 spudgirl  16   0 18464 9460 7068 S  0.0  2.5   0:01.17 x-session-manag
11828 spudgirl  16   0  3140 1020  804 S  0.0  0.3   0:00.02 ssh-agent
11831 spudgirl  15   0  2576  756  624 S  0.0  0.2   0:00.00 dbus-launch
11832 spudgirl  15   0  2156 1040  900 S  0.0  0.3   0:00.00 dbus-daemon
11834 spudgirl  16   0 12604 9940 1696 S  0.0  2.6   0:02.24 gconfd-2
11837 spudgirl  16   0  2432 1116  872 S  0.0  0.3   0:00.01 gnome-keyring-d
11841 spudgirl  16   0  6336 2860 2164 S  0.0  0.7   0:00.26 bonobo-activati
11843 spudgirl  16   0 19692 9360 6572 S  0.0  2.4   0:02.71 gnome-settings-
11846 spudgirl  15   0  2716 1500  888 S  0.0  0.4   0:09.79 gam_server
11858 spudgirl  16   0  5952 2504 1836 S  0.0  0.6   0:01.64 xscreensaver
11873 spudgirl  16   0 13816 8208 6244 S  0.0  2.1   0:20.14 metacity
11887 spudgirl  16   0 21584  12m 9148 S  0.0  3.4   0:07.08 gnome-panel
11889 spudgirl  16   0 36804  21m  12m S  0.0  5.6   0:22.91 nautilus
11891 spudgirl  16   0 17520 7516 5880 S  0.0  2.0   0:00.64 gnome-volume-ma
11897 spudgirl  15   0 18388 9840 7636 S  0.0  2.6   0:01.37 update-notifier
11899 spudgirl  16   0 38144 9044 6672 S  0.0  2.3   0:05.13 gnome-cups-icon
11903 spudgirl  16   0 12112 4300 3464 S  0.0  1.1   0:00.33 notification-da
11905 spudgirl  16   0 19316  10m 7968 S  0.0  2.8   1:27.99 wnck-applet
11909 spudgirl  15   0 52640 4716 3528 S  0.0  1.2   0:00.27 gnome-vfs-daemo
11914 spudgirl  16   0 19820 9208 6952 S  0.0  2.4   0:00.97 trashapplet
11916 spudgirl  16   0  2276  820  696 S  0.0  0.2   0:00.02 mapping-daemon
11932 spudgirl  16   0 17508 8080 6360 S  0.0  2.1   0:00.69 notification-ar
11934 spudgirl  15   0 20976  11m 8048 S  0.0  2.9   0:02.66 mixer_applet2
11936 spudgirl  16   0 22380 9.9m 7852 S  0.0  2.6   0:02.03 clock-applet
11943 spudgirl  24   0  4332 1640 1052 S  0.0  0.4   0:00.02 firefox
11954 spudgirl  25   0  4376 1672 1036 S  0.0  0.4   0:00.02 run-mozilla.sh
11959 spudgirl  15   0  157m  79m  17m S  0.0 21.2  15:13.27 firefox-bin
12402 spudgirl  15   0 47004  20m  12m S  0.0  5.3   3:01.96 gaim
12545 spudgirl  16   0  2284  720  580 S  0.0  0.2   0:00.00 gnome-pty-helpe
13250 spudgirl  16   0 25736 9248 7124 S  0.0  2.4   0:00.60 evolution-excha
17364 spudgirl  16   0 30760  12m 8420 S  0.0  3.4   0:02.18 gnome-terminal
17366 spudgirl  17   0  2280  716  580 S  0.0  0.2   0:00.00 gnome-pty-helpe
17367 spudgirl  16   0  4672 2056 1288 S  0.0  0.5   0:00.04 bash
17400 spudgirl  15   0  6536 5124 1096 S  0.0  1.3   0:00.00 esd
17401 spudgirl  15   0  2144  992  744 R  0.0  0.3   0:00.01 top

(sorry its so long, just pasting what I was told to, hehe)

My CPU is intel celeron 1.1 GHz 256kb cache
And yeah, already installed the newest version of Firefox, didn't really help any (other than it seems to randomly close more often).   I have sun java.

---

### Post by snowboard975 on 2006-03-30
I am experiencing slow speed problem, too. It happens when I leave my computer alone for more than twenty minutes. When I am back, it is reading my hard drive so eagerly that even move a mouse cursor will not move. This phenomenon usually continues for ten more minutes since I vibrate a mouse or press some keyboard buttons.

---

### Post by dcstar on 2006-03-30
[QUOTE=melissathespud]
.....
Any thoughts?  Suggestions?  Etc?[/QUOTE]
Using the 386 or 686 kernel?

---

### Post by melissathespud on 2006-03-30
[QUOTE=dcstar]Using the 386 or 686 kernel?[/QUOTE]

I should be using the 386 kernel...where do I confirm that?

---

### Post by 5-HT on 2006-03-30
[quote=melissathespud]I should be using the 386 kernel...where do I confirm that?[/quote] 
```
uname -r 
``` Look at the last three digits to the right.

---

### Post by towsonu2003 on 2006-03-30
Going bit by bit, I don't see a "probable cause" here... except RAM (376MB). Please read this all before trying things :)
> **melissathespud]df -h
Filesystem            Size  Used Avail Use% Mounted on
**/dev/mapper/Ubuntu-root** 37G  3.2G   32G  10% /
tmpfs                 189M     0  189M   0% /dev/shm
tmpfs                 189M   13M  176M   7% /lib/modules/2.6.12-10-386/volatile
/dev/hda1             228M   19M  197M   9% /boot
[/quote]
I'm unfamiliar with /dev/mapper/Ubuntu-root but it's big enough to hold everything, so there is no problem. 
[QUOTE=melissathespud]
free -m
             **total**       **used**       free     **shared    buffers     cached**
Mem:           **376        371**          5          **0          7         72**
-/+ buffers/cache:        290         85
Swap:         1123         **16**       1107
[/quote]
You do NOT have much RAM, so there may be a problem. As you see, all of the RAM is used. And it is using a little bit of swap (which will slow things down when more swap is being used later on). 

[QUOTE=melissathespud]
 top -b -n 1
top - 19:35:29 up 19:19,  3 users,  load average: 0.90, 0.70, 0.62
Tasks:  90 total,   1 running,  89 sleeping,   0 stopped,   0 zombie
**Cpu(s)**: **20.0% us**,  0.6% sy,  0.0% ni, **79.0% id**,  0.3% wa,  0.0% hi,  0.0% si
Mem:    **385304k** total,   **380332k** used,     4972k free,     7832k buffers
Swap:  1150968k total,    17256k used,  1133712k free,    74684k cached
[/quote]
Your cpu is idle (79%), so I am guessing you were not experiencing the slow down right then? If this is so, output above makes sense. I am guessing that during the slow downs, the data written to swap (ie data being swapped) increases. Hence causing slow downs. Try xubuntu to see if the slow down is the same. To try xubuntu (internet connection required):
```

sudo apt-get update
sudo apt-get install xubuntu-desktop

```
Log out of gnome (no need to reboot), choose "xfce" from "sessions" menu, then login. Try that for a while to see if slow downs happen there as well. xubuntu gives you xfce, which is a leightweight desktop environment (read: less bloated gnome, uses less memory and less cpu). Report back  said:**
> 
  PID USER      PR  NI  VIRT  RES  SHR S %CPU **%MEM**    TIME+  COMMAND
15942 spudgirl 16 0 255m 73m 14m S 3.9 **19.7** 8:21.64 java_vm
11790 root 15 0 140m 62m 12m S 0.0 **16.7** 141:42.42 Xorg
11959 spudgirl 15 0 157m 79m 17m S 0.0 **21.2** 15:13.27 firefox-bin

I outlined the programs that seem to be causing trouble: trouble with the memory. This conforms with my initial diagnosis I guess? In XFCE, compare the performance of firefox to epiphany in sites where you experience system slow downs. My comparisons show that system doesn't slow down in digg.com (heavy javascript use) when using epiphany rather than firefox. get epiphany with ```
sudo apt-get install epiphany-browser
```
[QUOTE=melissathespud]
(sorry its so long, just pasting what I was told to, hehe)
[/quote]
lol :PpPpP
[QUOTE=melissathespud]
My CPU is intel celeron 1.1 GHz 256kb cache[/quote]
I'm not sure but that seems to be a slow one? Xfce might help with that as well. Also, if you are not using an 686 kernel, try it out:
```

uname -r

``` will tell you if you are using 386 or 686. if it says 386, do the following and reboot:
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get install linux-686

```
[QUOTE=melissathespud]
And yeah, already installed the newest version of Firefox, didn't really help any (other than it seems to randomly close more often).   I have sun java.[/QUOTE]
Before doing any of the above, try firefox with the following from a terminal:
```

firefox --safe-mode
``` and see if there is system slow down. If no, the problem is with your profile/extensions/theme (happens frequently, called profile corruption or extension conflict)

So, to summarize, do the following (in this order) to see if any helps: 
1. run firefox with firefox --safe-mode, see if slow down happens
2. install linux-686 and reboot, see if slow down happens
3. install xubuntu-desktop and log on to xfce (instead of gnome), see if slow down happens
4. use epiphany instead of firefox in xfce, compare speeds

In each step, once you see it's slowing down, open up a terminal and type ```
top
``` and observe what's using most of the memory and/or cpu. My guess is java+xorg+firefox will be eating up your memory. If I'm right, xfce+epiphany will solve the problem. 

I am hoping slow downs will stop at step 1, which will only require a new profile and a few but more compatible extensions...

For this, I use something called "conky". It is a great way to monitor the system. Check this out if you have time: [http://ubuntuforums.org/showthread.php?t=110535&highlight=conky](http://ubuntuforums.org/showthread.php?t=110535&highlight=conky) It has screenshots and sample configuration files. You will be able to see what your system is doing in real time (and become a little bit more geek&paranoid). 

If xfce doesn't speed up things for you, I don't think I will know what's going on. We'll think of something if that's the case. Video driver is the first thing that comes to mind. We'll se at that point...

Edit: wow this was long :Pp

---

### Post by dcstar on 2006-03-31
[QUOTE=melissathespud]I should be using the 386 kernel...where do I confirm that?[/QUOTE]

The 386 kernel is for legacy machines from the late 1980's, the 686 kernel works with anything later than the original Pentium (early 1990's).

If you use a 386 kernel you are only limiting the potential of your system, AMD users should use the K7 kernel.

---


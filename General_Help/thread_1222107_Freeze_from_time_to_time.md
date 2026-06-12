---
title: "Freeze from time to time"
date: 2009-07-24
forum: General Help
---

### Post by merciadriluca on 2009-07-24
Hello,

On my Debian PC, and, during some specific actions, everything seems to freeze. For example, when I use the Thunderbird's Debian's equivalent, and that I send a signed e-mail, the window (and its relative application) freezes, and the only way to close it is to kill the relative process, or the relative processes. The problem becomes really hard when I'm listening to music, as the playing's ``place'' is repeated 20 or 30 times, before going to the following 1/10th of the second, the whole thing giving a played music that you wouldn't like to listen to.
The music is played perfectly when no such operation is performed.

That is very annoying, and I experienced this with Ubuntu, whatever the version, and Debian, using many different kernels, being on the cutting edge of last upgrades when necessary. I think that my hardware is (partially) not supported. 

However, it is not really new. Here is my config:

Intel Core 2 Quad Q9450@2.66Ghz * 4,
Asus P5K/EPU.

Any idea about what I could do? I do not understand why such a problem is occuring. Though, my BIOS is upgraded!

---

### Post by merciadriluca on 2009-07-25
Here are some fresh pieces of info:

Memtest gives no error, but only when I choose ``old version,'' at boot. Actually, both other choices (current version, no SMP, or current version, experimental SMP) bug: the no SMP cersion reboots after only few seconds, and the other freezes, and I have to turn off the PC!

---

### Post by SoftBear on 2009-07-25
Sorry, but what is the size of your RAM? and Swap?
What kernels you've been trying?
How many process? if it possible: what exactly you've been runing? and is your OSs are clean when it freezes? (I mean, have you installed some extra applications?)
Which version of Ubuntu is installed there?

---

### Post by merciadriluca on 2009-07-25
> **SoftBear said:**
> Sorry, but what is the size of your RAM?
2*2048
> **SoftBear said:**
>  and Swap?

3500
> 
What kernels you've been trying?

2.6.26-2-686 and lower.

> 
How many process? if it possible: what exactly you've been runing? and is your OSs are clean when it freezes? (I mean, have you installed some extra applications?)
In both cases: i) After installing Debian, with nothing more, it already bugs; ii) After having installed various programs, such as BOINC, vlc, various codecs, and different libraries, it bugs. 

Thanks.

---

### Post by SoftBear on 2009-07-25
Sorry for repeating, but "How many process are ran?"

---

### Post by DeMus on 2009-07-25
You answered you use 2.6.28-2 and lower as kernel versions. Try updating to the newest 2.6.30. I also had problems with 2.6.28-11 until -13. Now I use the 2.6.30 and all is well. No problems whatsoever. You can use Synaptic to upgrade.

---

### Post by SoftBear on 2009-07-25
> **DeMus said:**
> You answered you use 2.6.28-2 and lower as kernel versions. Try updating to the newest 2.6.30. I also had problems with 2.6.28-11 until -13. Now I use the 2.6.30 and all is well. No problems whatsoever. You can use Synaptic to upgrade.

I can suppose you are right, but Be careful, When I updated on 2.6.30, I had some problems... Be careful.

---

### Post by merciadriluca on 2009-07-25
> **SoftBear said:**
> I can suppose you are right, but Be careful, When I updated on 2.6.30, I had some problems... Be careful.

I had other problems, as SoftBear seemed to have, with this new kernel.

How many processes? Here it is:

```


  PID TTY          TIME CMD
    1 ?        00:00:01 init
    2 ?        00:00:00 kthreadd
    3 ?        00:00:00 migration/0
    4 ?        00:00:00 ksoftirqd/0
    5 ?        00:00:00 watchdog/0
    6 ?        00:00:00 migration/1
    7 ?        00:00:00 ksoftirqd/1
    8 ?        00:00:00 watchdog/1
    9 ?        00:00:00 migration/2
   10 ?        00:00:00 ksoftirqd/2
   11 ?        00:00:00 watchdog/2
   12 ?        00:00:00 migration/3
   13 ?        00:00:00 ksoftirqd/3
   14 ?        00:00:00 watchdog/3
   15 ?        00:00:05 events/0
   16 ?        00:00:04 events/1
   17 ?        00:00:04 events/2
   18 ?        00:00:04 events/3
   19 ?        00:00:00 khelper
   54 ?        00:00:00 kblockd/0
   55 ?        00:00:00 kblockd/1
   56 ?        00:00:00 kblockd/2
   57 ?        00:00:00 kblockd/3
   59 ?        00:00:00 kacpid
   60 ?        00:00:00 kacpi_notify
  152 ?        00:00:00 kseriod
  201 ?        00:00:00 pdflush
  202 ?        00:00:00 pdflush
  203 ?        00:00:00 kswapd0
  204 ?        00:00:00 aio/0
  205 ?        00:00:00 aio/1
  206 ?        00:00:00 aio/2
  207 ?        00:00:00 aio/3
  654 ?        00:00:00 ksuspend_usbd
  655 ?        00:00:00 khubd
  841 ?        00:00:00 khpsbpkt
  865 ?        00:00:00 knodemgrd_0
  900 ?        00:00:00 ata/0
  901 ?        00:00:00 ata/1
  902 ?        00:00:00 ata/2
  903 ?        00:00:00 ata/3
  904 ?        00:00:00 ata_aux
  918 ?        00:00:00 scsi_eh_0
  919 ?        00:00:00 scsi_eh_1
 1001 ?        00:00:00 scsi_eh_2
 1002 ?        00:00:00 scsi_eh_3
 1107 ?        00:00:00 scsi_eh_4
 1109 ?        00:00:00 scsi_eh_5
 1232 ?        00:00:01 kjournald
 1308 ?        00:00:00 udevd
 1997 ?        00:00:00 kpsmoused
 2429 ?        00:00:00 portmap
 2441 ?        00:00:00 rpc.statd
 2455 ?        00:00:00 rpciod/0
 2456 ?        00:00:00 rpciod/1
 2457 ?        00:00:00 rpciod/2
 2458 ?        00:00:00 rpciod/3
 2475 ?        00:00:00 nfsiod
 2498 ?        00:00:00 rpc.idmapd
 2764 ?        00:00:00 kondemand/0
 2766 ?        00:00:00 kondemand/1
 2767 ?        00:00:00 kondemand/2
 2768 ?        00:00:00 kondemand/3
 2818 ?        00:00:00 rsyslogd
 2830 ?        00:00:00 acpid
 2840 ?        00:00:00 dbus-daemon
 2852 ?        00:00:00 avahi-daemon
 2853 ?        00:00:00 avahi-daemon
 2924 ?        00:00:00 cupsd
 3194 ?        00:00:00 exim4
 3203 ?        00:00:00 fah6
 3274 ?        00:00:00 FahCore_78.exe
 3283 ?        00:00:00 hddtemp
 3292 ?        00:00:00 kerneloops
 3321 ?        00:00:00 lockd
 3322 ?        00:00:00 nfsd4
 3323 ?        00:00:00 nfsd
 3324 ?        00:00:00 nfsd
 3325 ?        00:00:00 nfsd
 3326 ?        00:00:00 nfsd
 3327 ?        00:00:00 nfsd
 3328 ?        00:00:00 nfsd
 3329 ?        00:00:00 nfsd
 3330 ?        00:00:00 nfsd
 3332 ?        00:00:00 FahCore_78.exe
 3333 ?        00:31:09 FahCore_78.exe
 3334 ?        00:00:00 FahCore_78.exe
 3337 ?        00:00:00 rpc.mountd
 3348 ?        00:00:00 inetd
 3398 ?        00:00:00 nmbd
 3400 ?        00:00:00 smbd
 3421 ?        00:00:00 winbindd
 3432 ?        00:00:00 winbindd
 3433 ?        00:00:00 hald
 3434 ?        00:00:00 hald-runner
 3437 ?        00:00:00 winbindd
 3438 ?        00:00:00 winbindd
 3443 ?        00:00:00 smbd
 3455 ?        00:00:00 dhclient3
 3489 ?        00:00:00 hald-addon-inpu
 3496 ?        00:00:00 hald-addon-cpuf
 3497 ?        00:00:00 hald-addon-acpi
 3499 ?        00:00:00 hald-addon-stor
 3511 ?        00:00:00 hald-addon-stor
 3513 ?        00:00:00 hald-addon-stor
 3515 ?        00:00:00 hald-addon-stor
 3527 ?        00:00:00 gdm
 3531 ?        00:00:00 gdm
 3536 tty7     00:03:25 Xorg
 3540 ?        00:00:00 system-tools-ba
 3563 ?        00:00:00 atalkd
 3579 ?        00:00:02 gconfd-2
 3581 ?        00:00:00 gnome-keyring-d
 3582 ?        00:00:00 x-session-manag
 3630 ?        00:00:00 dbus-launch
 3631 ?        00:00:00 dbus-daemon
 3637 ?        00:00:00 seahorse-agent
 3640 ?        00:00:01 gnome-settings-
 3660 ?        00:00:02 gnome-screensav
 3661 ?        00:00:01 metacity
 3662 ?        00:00:03 gnome-panel
 3665 ?        00:00:01 nautilus
 3671 ?        00:00:00 bonobo-activati
 3674 ?        00:00:00 bluetooth-apple
 3684 ?        00:00:00 gnome-vfs-daemo
 3685 ?        00:00:00 system-config-p
 3689 ?        00:00:00 kerneloops-appl
 3690 ?        00:00:00 gnome-volume-ma
 3697 ?        00:00:00 gnome-power-man
 3716 ?        00:00:03 sensors-applet
 3722 ?        00:00:00 mapping-daemon
 3729 ?        00:00:00 mixer_applet2
 3732 ?        00:00:01 cpufreq-applet
 3737 ?        00:01:04 multiload-apple
 3739 ?        00:00:00 gweather-applet
 3747 ?        00:00:00 icedove
 3759 ?        00:00:00 run-mozilla.sh
 3764 ?        00:00:32 icedove-bin
 3793 ?        00:00:00 afpd
 3795 ?        00:00:00 papd
 3808 ?        00:00:00 atd
 3828 ?        00:00:00 cron
 3845 tty1     00:00:00 getty
 3846 tty2     00:00:00 getty
 3847 tty3     00:00:00 getty
 3848 tty4     00:00:00 getty
 3849 tty5     00:00:00 getty
 3850 tty6     00:00:00 getty
 3864 ?        00:00:01 gnome-terminal
 3866 ?        00:00:00 gnome-pty-helpe
 3867 pts/0    00:00:00 bash
 3879 pts/0    00:00:00 su
 3880 pts/0    00:00:00 bash
 3881 pts/1    00:00:00 bash
 3892 pts/1    00:00:33 vlc
 3936 ?        00:00:00 su
 3938 ?        00:00:00 bash
 3939 ?        00:00:00 bash
 3940 ?        00:00:17 boincmgr
 3944 ?        00:00:02 boinc
 3945 ?        00:24:38 orcaAlpha_5.01_
 3946 ?        00:25:10 orcaAlpha_5.01_
 3947 ?        00:00:01 hadam3p_6.06_i6
 3948 ?        00:24:43 setiathome_6.03
 3961 ?        00:26:51 hadam3p_um_6.06
 4099 pts/3    00:00:00 bash
 4117 pts/3    00:00:00 su
 4119 pts/3    00:00:00 bash
 4153 ?        00:09:46 firefox-bin
 4207 pts/4    00:00:00 bash
 4229 pts/4    00:00:00 su
 4230 pts/4    00:00:00 bash
 4305 pts/5    00:00:00 bash
 4318 pts/5    00:00:00 ps



```

Dunno precisely how much. Notice that grid-related processes are launched, but the problem appears whatever is launched, even when Debian is ran as bare as it can be ran.

**DeMus**, which problems were you experiencing before adopting a new kernel?

---

### Post by SoftBear on 2009-07-25
I'm sorry, one more question: which version of linux do you use? (x64 or x86)?

---

### Post by merciadriluca on 2009-07-25
x86. Hope it makes things easier.

---

### Post by SoftBear on 2009-07-26
Maybe my suggestion looks like quite stupid, but: Did you try to use x64 version?

Few messages bellow you've said that only few programs are installed and it starts freezing. - what about absolutely "virgin" Ubuntu without any extras?!
Are desctop-effects ran?

Could you repeat which Ubuntu version is installed? (9.04 ?) [If yes, then try to install 8.10]

In ubuntu exists a program calls SystemMonitor, there shows Processes and How CPU being busy...
Look at the list and find processes that use more than 50% (30%) of CPU time.... and make summary :).

Hope we will help you :)

---

### Post by merciadriluca on 2009-07-26
> **SoftBear said:**
> Maybe my suggestion looks like quite stupid, but: Did you try to use x64 version?
It is actually not stupid at all. I had also thought of it, but I would like to do this if there is no other solution. I would have many other problems if I use x64, for complicated reasons (we all now how a Linux system can be fragile).


> **SoftBear said:**
> what about absolutely "virgin" Ubuntu without any extras?!
That is what I wanted to say. I had freezes with ``virgin'' Ubuntu and Debian.

> **SoftBear said:**
> Are desctop-effects ran?
No.

> **SoftBear said:**
> Could you repeat which Ubuntu version is installed? (9.04 ?) [If yes, then try to install 8.10]
I tried with 9.04, 8.10, and I am now using **Debian **Lenny.



> **SoftBear said:**
> In ubuntu exists a program calls SystemMonitor, there shows Processes and How CPU being busy...
Look at the list and find processes that use more than 50% (30%) of CPU time.... and make summary :).
After many looks, I realize that it clearly does not depend **only **upon the CPU usage. Though, I notice that when, e.g. Thunderbird sends a mail and that another programs are running, and that Thunderbird freezes, there is a magic thing before freezing: the ``memory use'' grows more and more (e.g. 19 - > 20 -> 21 -> 22), unstoppingly. It becomes so important that Swap space is used before my 3.2 (actually 4, but as I use x86, 4*1024 are not used fully) Go are used.
When ``memory'' is high (even if, when looking at the info in the system monitor, it is not as highly used as it is written in the bar), and that it reaches an using peak, Thunderbird is directly closed. Music finds its way to recover from the freeze, and everything becomes normal. Unfortunately, that is not what I want, as it is better if my mail is sent.

Any idea?

---

### Post by SoftBear on 2009-07-26
I need more time to think.... When I get some ideas - I'll tell you.

---

### Post by merciadriluca on 2009-07-26
> **SoftBear said:**
> I need more time to think.... When I get some ideas - I'll tell you.

Thanks. Waiting for your answer.

---

### Post by SoftBear on 2009-07-29
I'm sorry but I have no idea yet...
If I'll invent something - I'll tell you.

---

### Post by merciadriluca on 2009-07-30
No problem. 

I looked at /var/log/kern.log, but it did not show anything interesting.

Sb. told me this:
[quote="shoof"]If you can make it crash then try starting Icedove from a terminal to see if it spits out any information as it crashes.  You can also try removing enigmail and making Icedove crash to see if it is Icedove itself or Enigmail that is causing it.  Once you figure out which program is causing it then you can run from a terminal 'strace icedove'  (you may have to install strace first) then make it crash, this will spit out some information that you may not understand.  Either way you will probably want to file a bug report against icedove or enigmail and include the strace output, the developers will be able to use it.[/quote]
From a terminal, it only writes ``*** Gnome Registry Session: yes.'' ~50 times, and nothing more.
Definitely, the problem is coming from Enigmail. When I deactivate enigmail, it works well. Using strace with Enigmail, it also display `*** Gnome Registry Session: yes,'' before the bug, but nothing during the bug. strace shows information when I kill the process ``icedove;'' here is the output:
```

[...]
 *** Gnome Registry Session: yes.
 *** Gnome Registry Session: yes.
 *** Gnome Registry Session: yes.
/usr/lib/icedove/run-mozilla.sh: line 131:  4220 Killed                  "$prog" ${1+"$@"}
[{WIFEXITED(s) && WEXITSTATUS(s) == 137}], 0) = 4215
rt_sigprocmask(SIG_SETMASK, [], NULL, 8) = 0
--- SIGCHLD (Child exited) @ 0 (0) ---
waitpid(-1, 0xbff235f8, WNOHANG)        = -1 ECHILD (No child processes)
sigreturn()                             = ? (mask now [])
rt_sigaction(SIGINT, {SIG_DFL}, {0x807ef30, [], 0}, 8) = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
read(255, "exitcode=$?\n\n## Stop addon script"..., 5268) = 91
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
open("/home/merciadriluca/.icedove/init.d/", O_RDONLY|O_NONBLOCK|O_LARGEFILE|O_DIRECTORY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
open("/usr/lib/icedove/init.d/", O_RDONLY|O_NONBLOCK|O_LARGEFILE|O_DIRECTORY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
stat64("/home/merciadriluca/.icedove/init.d/K*", 0xbff2319c) = -1 ENOENT (No such file or directory)
rt_sigprocmask(SIG_SETMASK, [], NULL, 8) = 0
rt_sigprocmask(SIG_BLOCK, [CHLD], [], 8) = 0
rt_sigprocmask(SIG_SETMASK, [], NULL, 8) = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
stat64("/usr/lib/icedove/init.d/K*", 0xbff2319c) = -1 ENOENT (No such file or directory)
rt_sigprocmask(SIG_SETMASK, [], NULL, 8) = 0
rt_sigprocmask(SIG_BLOCK, [CHLD], [], 8) = 0
rt_sigprocmask(SIG_SETMASK, [], NULL, 8) = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
rt_sigprocmask(SIG_SETMASK, [], NULL, 8) = 0
exit_group(137)                         = ?

```

There is more to it: if I do not kill ``icedove'' (debian seems not to kill it these times, as it does not use the whole memory), let the screen go dark, my keyboard is kept blocked, nothing responds (even emergency keys), and I have to shutdown the PC using its power button!!

---

### Post by moster on 2009-07-30
> **merciadriluca said:**
> Hello,

On my Debian PC, and, during some specific actions, everything seems to freeze. For example, when I use the Thunderbird's Debian's equivalent, and that I send a signed e-mail, the window (and its relative application) freezes, and the only way to close it is to kill the relative process, or the relative processes. The problem becomes really hard when I'm listening to music, as the playing's ``place'' is repeated 20 or 30 times, before going to the following 1/10th of the second, the whole thing giving a played music that you wouldn't like to listen to.
The music is played perfectly when no such operation is performed.

That is very annoying, and I experienced this with Ubuntu, whatever the version, and Debian, using many different kernels, being on the cutting edge of last upgrades when necessary. I think that my hardware is (partially) not supported. 

However, it is not really new. Here is my config:

Intel Core 2 Quad Q9450@2.66Ghz * 4,
Asus P5K/EPU.

Any idea about what I could do? I do not understand why such a problem is occuring. Though, my BIOS is upgraded!

I have similar MBO to yours. I have asus P5KPL. I had that exactly problems in Ubuntu 8.10. I do not know what kernel that was... but, when I installed Jaunty that problem waas gone. Here is current situation and I can conform I had never again those issues.
```
Linux moster-desktop 2.6.28-14-generic #47-Ubuntu SMP Sat Jul 25 00:28:35 UTC 2009 i686 GNU/Linux
```
Maybe it is not even kerne.. maybe it is VGA driver or sound.. I doubt anybody really know. Point is, go up. Use newer kernel and everything else.

---

### Post by merciadriluca on 2009-07-30
> **moster said:**
> I have similar MBO to yours. I have asus P5KPL. I had that exactly problems in Ubuntu 8.10. I do not know what kernel that was...

It seems to be linked to the motherboard, isn't it?

> **moster said:**
> [...] when I installed Jaunty that problem waas gone. Here is current situation and I can conform I had never again those issues.
```
Linux moster-desktop 2.6.28-14-generic #47-Ubuntu SMP Sat Jul 25 00:28:35 UTC 2009 i686 GNU/Linux
```
Maybe it is not even kerne.. maybe it is VGA driver or sound.. I doubt anybody really know. Point is, go up. Use newer kernel and everything else.
Unfortunately, I had tried Jaunty, and it was clearly worse! The situation was incredibly unstable. :(

However, I'm happy to learn that I'm not the only person who has these problems.

---

### Post by moster on 2009-07-30
> **merciadriluca said:**
> It seems to be linked to the motherboard, isn't it?

Unfortunately, I had tried Jaunty, and it was clearly worse! The situation was incredibly unstable. :(

However, I'm happy to learn that I'm not the only person who has these problems.

You have even worse experience with jaunty?? Huh. If those problems are obvius, then you should maybe load Ubuntu 9.10 Carmic koala alpha on USB stick and see what there is happening.

Maybe some option in your BIOS is causing some incompatibility. Maybe you just need to turn off ACPI 2.0 or something like that...

I thought if I buy Intel I will not have problems because Intel is "friendly". I see much problems connected to intel hardware, from vga to chipsets. I do not know how to explain that exactly.

Currently, I do not have freezing problem but sluggish performance problem under high I/O. Oh, where is end, did I not suffer enough already.. :D

p.s.
On some crappy nvidia all-in-one MBO everything is flying. Unfortunely, CPU on that board is AMD and it is twice slower then mine so I will not use it.

---

### Post by merciadriluca on 2009-07-30
> **moster said:**
> You have even worse experience with jaunty?? Huh.

Clearly.

> **moster said:**
> If those problems are obvious, then you should maybe load Ubuntu 9.10 Carmic koala alpha on USB stick and see what there is happening.

The situation is bearable now, but I will think about it if necessary.


> **moster said:**
> Maybe some option in your BIOS is causing some incompatibility. Maybe you just need to turn off ACPI 2.0 or something like that...
I had already tried. :(

Thanks anyway for your help.

---

### Post by moster on 2009-07-30
Sorry, If I underestimate your knowledge. Let me take a peek into your hardware to see difference. This command will generate file in your home dir. I will add mine too. Attach also anything may find important.

```
sudo lshw -html > hardware.html
```

---

### Post by merciadriluca on 2009-07-30
Here you are.

I notice that you are using a Dual-Core. Is the fact of using more than 1 processor on our machines not the basis of our problem? I know Linux OS are able to deal with lots of CPU's (e.g. servers), but it can be less supported under Ubuntu, can't it?

---

### Post by moster on 2009-07-30
> **merciadriluca said:**
> Here you are.

I notice that you are using a Dual-Core. Is the fact of using more than 1 processor on our machines not the basis of our problem? I know Linux OS are able to deal with lots of CPU's (e.g. servers), but it can be less supported under Ubuntu, can't it?

Single core CPUs are history. Ubuntu are perfectly fine with our CPUs and your is beast :)

I look at your hardware and I can see only one thing I suspect is somehow connected to this problem.
Your ACX 111 54Mbps Wireless. Do you run it under NDIS wrapper, or do linux have native support to it? If used trough NDIS wrapper it could be source of your problems.

Ok, I have time so I will little further explain. I had Netgear usb wireless before and it gave me so much so called "ghost" problems that I cannot describe. But I could get it run trought ndis wrapper. I got rid of those netgear and get Jaunty in same time. And I forgot about those problems. Now when I see yours, I remembered.

I strongly urge you to use different wlan adapter and see if you have  problems then. Your and my problem are just scary similar, yet nobody can explain it.

---

### Post by merciadriluca on 2009-07-30
Thanks for your answer. I never use my wlan adapter, and it is supported natively (I had also problems with NDIS wrapper, and I promised to myself to never make too much with it). I would have preferred saying "it was the problem. Thanks." :(

As you say, our problems are similar, but I don't know if they are due to the same reasons.

---


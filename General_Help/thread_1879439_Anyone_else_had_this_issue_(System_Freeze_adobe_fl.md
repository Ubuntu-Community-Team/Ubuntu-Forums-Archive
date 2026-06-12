---
title: "Anyone else had this issue? (System Freeze adobe flash related)"
date: 2011-11-11
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2011-11-11
for the past couple months when i leave a page that has adobe flash on it sometimes everything freezes all i have in my mouse and the course is froze but still moves
so far i have only had this happen with videos
i am running lucid and using a nvidia video card with the latest stable driver
i am using the last release candidate of flash since i know that the latest release they killed hardware acceleration in it even as a unsupported feature
i just had it freeze 2 times in a row today both videos were hosted on megavideo i have also had this happen on youtube

if anyone else has encountered this issue has you found a solution?

---

### Post by ikt on 2011-11-11
> **pqwoerituytrueiwoq said:**
> if anyone else has encountered this issue has you found a solution?

Have you used flash-aid to ensure you are running the latest version?

---

### Post by pqwoerituytrueiwoq on 2011-11-11
I am using the release candidate for the current version 11,0,1,129 the current version is 11.1.102.55
adobe completely disabled hardware acceleration as of version 11.1.102.55 even via the override option in flash aid

i am intentionally not using the latest version of adobe flash

---

### Post by lechien73 on 2011-11-11
I think I'd try completely purging the flash player and re-installing. I had a lot of problems with flash on 64-bit Ubuntu, and eventually resorted to using "Square", Adobe's codename for a 64-bit flash release.

I don't know if it will help you, but I blogged about it extensively [here]("http://blog.mattrudge.net/2010/09/23/new-64-bit-flash-installer-for-ubuntu-10-04-lucid-lynx/"), [here]("http://blog.mattrudge.net/2011/04/21/fullscreen-flash-freezing-fix/"), and [here]("http://blog.mattrudge.net/2010/05/03/installing-flash-player-on-ubuntu-10-04-64-bit/"). Some of the solutions might assist you.

---

### Post by pqwoerituytrueiwoq on 2011-11-11
the current version of flash is the 1st release to offer 64bit support officially
the version i am using requires no plugin wrapper
i am using the final developmental release of flash before the current release that support 64bit and if the flash deveopler was correct in saying that as of 11.1.102.55 hardware acceleration was completely disabled since i am using the version right before that one is should still have hardware acceleration they said they disabled it over coroners for security but if it can't get the job done what is the point

---

### Post by pqwoerituytrueiwoq on 2011-11-25
this useful?

```
~$ cat /var/log/Xorg.1.log
X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-28-server x86_64 Ubuntu
Current Operating System: Linux lucid-desktop 2.6.35-25-generic #44~lucid1-Ubuntu SMP Tue Jan 25 19:17:25 UTC 2011 x86_64
Kernel command line: root=UUID=a7bc74de-0ab3-48f8-a159-693f8bccb3cb ro quiet splash ipv6.disable=1 nomodeset video=uvesafb:mode_option=1280x800-24,mtrr=3,scroll=ywrap 
Build Date: 20 October 2011  03:03:02PM
xorg-server 2:1.7.6-2ubuntu7.10 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.16.4
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.1.log", Time: Fri Nov 25 23:03:31 2011
(==) Using config file: "/etc/X11/xorg.conf"
(==) Using config directory: "/usr/lib/X11/xorg.conf.d"
(==) ServerLayout "Layout0"
(**) |-->Screen "Screen0" (0)
(**) |   |-->Monitor "Monitor0"
(**) |   |-->Device "Device0"
(**) |-->Input Device "Keyboard0"
(**) |-->Input Device "Mouse0"
(**) Option "Xinerama" "0"
(==) Automatically adding devices
(==) Automatically enabling devices
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
    Entry deleted from font path.
(==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
    built-ins
(==) ModulePath set to "/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
(WW) AllowEmptyInput is on, devices using drivers 'kbd', 'mouse' or 'vmmouse' will be disabled.
(WW) Disabling Keyboard0
(WW) Disabling Mouse0
(II) Loader magic: 0x7cb840
(II) Module ABI versions:
    X.Org ANSI C Emulation: 0.4
    X.Org Video Driver: 6.0
    X.Org XInput driver : 7.0
    X.Org Server Extension : 2.0
(--) using VT number 8


[B]Fatal server error:
xf86OpenConsole: VT_WAITACTIVE failed: Interrupted system call[/B]


Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 
Please also check the log file at "/var/log/Xorg.1.log" for additional information.

 ddxSigGiveUp: Closing log
```

---

### Post by pqwoerituytrueiwoq on 2011-12-04
is there any command to kill Xorg?
none of theses worked on it when it locked up
when it locks up the only access i have is via ssh
```
sudo pkill -f Xorg
sudo pkill -U 1419
killall gdm
sudo killall gdm
sudo killall Xorg
```

```
top - 11:06:19 up  2:16,  1 user,  load average: 1.03, 1.21, 1.01
Tasks: 227 total,   2 running, 223 sleeping,   0 stopped,   2 zombie
Cpu(s): 25.1%us,  0.1%sy,  0.0%ni, 74.7%id,  0.1%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:  12330888k total,  2307224k used, 10023664k free,   141880k buffers
Swap: 16779888k total,        0k used, 16779888k free,   737584k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 1419 root      20   0  169m  49m  15m R  100  0.4  17:02.37 Xorg               
 4621 chad      20   0 19280 1292  888 R    1  0.0   0:00.05 top                
  109 root      20   0     0    0    0 S    0  0.0   0:04.66 kondemand/2        
 3656 chad      20   0 18080 5596 4604 S    0  0.0   0:14.38 npviewer.bin       
    1 root      20   0 23852 1972 1268 S    0  0.0   0:00.90 init               
    2 root      20   0     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      20   0     0    0    0 S    0  0.0   0:00.09 ksoftirqd/0        
    4 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/0        
    5 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/1        
    7 root      20   0     0    0    0 S    0  0.0   0:00.13 ksoftirqd/1        
    8 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/1         
    9 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/2        
   10 root      20   0     0    0    0 S    0  0.0   0:00.07 ksoftirqd/2        
   11 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/2
```

---

### Post by d17ub on 2011-12-13
I've had a similar thing with freezing on Maverick 10.10 when leaving a page with flash for the last couple of weeks. 

I don't know how to do diagnostic things but I thought some of the problem might be with adobe air esp. since there were about 5 or 6 zombie processes associated with it showing up on system monitor. I uninstalled air from software centre but 6 adobe air zombie processes are still showing up. I don't know what these are or how to get rid of them and they have just horribly mutated into a bunch of other zombie processes (about 20 of them) named 'sh'. Any advice?

---

### Post by pqwoerituytrueiwoq on 2011-12-23
i do not have adobe air and there is no 64bit version advailable

---


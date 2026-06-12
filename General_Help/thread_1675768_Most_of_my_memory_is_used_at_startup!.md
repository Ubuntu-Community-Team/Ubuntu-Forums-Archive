---
title: "Most of my memory is used at startup!"
date: 2011-01-26
forum: General Help
---

### Post by erelsgl on 2011-01-26
I have Intel with 2 GB memory, but when I start my Ubuntu 10.04, which I just installed, without running any process, I already have 1.5 GB used. When I start Firefox, it rises to 1.9 GB:

```

erelsgl@ubuntu:~$ top

top - 11:44:25 up 28 min,  2 users,  load average: 0.29, 0.43, 0.39
Tasks: 162 total,   1 running, 161 sleeping,   0 stopped,   0 zombie
Cpu(s):  0.5%us,  0.3%sy,  0.0%ni, 99.2%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   2048288k total,  1957740k used,    90548k free,   705732k buffers
Swap:   261112k total,        0k used,   261112k free,   776832k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
  966 root      20   0  115m  18m 8268 S    2  0.9   1:32.73 Xorg               
 1509 erelsgl   20   0  216m  18m  11m S    1  0.9   0:02.73 gnome-terminal     
 1568 erelsgl   20   0  686m 138m  31m S    1  6.9   2:52.69 firefox-bin        
   45 root      20   0     0    0    0 S    0  0.0   0:00.69 scsi_eh_0          
    1 root      20   0 23792 1956 1256 S    0  0.1   0:00.64 init               
    2 root      20   0     0    0    0 S    0  0.0   0:00.01 kthreadd           
    3 root      RT   0     0    0    0 S    0  0.0   0:00.01 migration/0        
    4 root      20   0     0    0    0 S    0  0.0   0:00.04 ksoftirqd/0        
    5 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT   0     0    0    0 S    0  0.0   0:00.01 migration/1        
    7 root      20   0     0    0    0 S    0  0.0   0:00.04 ksoftirqd/1        
    8 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/1         
    9 root      20   0     0    0    0 S    0  0.0   0:00.03 events/0           
   10 root      20   0     0    0    0 S    0  0.0   0:00.07 events/1           
   11 root      20   0     0    0    0 S    0  0.0   0:00.00 cpuset             
   12 root      20   0     0    0    0 S    0  0.0   0:00.00 khelper            
   13 root      20   0     0    0    0 S    0  0.0   0:00.00 netns              

```

How can I debug this problem?

Thank you

---

### Post by erelsgl on 2011-01-26
P.S.
Sysinfo shows a completely different picture:

Total memory - 2000 MiB
   Free: 76%
Swap total - 254 MiB
   Free: 100%

Cached - 770 MiB
Active - 444 MiB
Inactive - 1333 MiB


What's going on?

---

### Post by themusicalduck on 2011-01-26
That memory isn't actually being used up. Linux caches the memory so that it can be used quickly when it is needed.

Run the command free -m in a terminal and look at -/+ buffers/cache. That shows you how much is used and how much is free.

Or if you're running the normal Ubuntu desktop then look at System Monitor, Resources tab.

---

### Post by erelsgl on 2011-01-26
This is what I see after I startup and start Firefox (before I start Firefox, the "used" is about 1400 - less than now but still very high):

```
erelsgl@ubuntu:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          2000       1957         42          0        663        832
-/+ buffers/cache:        460       1539
Swap:          254          0        254

```

---

### Post by erelsgl on 2011-01-26
Maybe this is also useful, although I don't really understand what this means:

```
erelsgl@ubuntu:~$ initctl list
alsa-mixer-save stop/waiting
avahi-daemon start/running, process 779
mountall-net stop/waiting
rc stop/waiting
rsyslog start/running, process 748
screen-cleanup stop/waiting
tty4 start/running, process 910
udev start/running, process 335
upstart-udev-bridge start/running, process 333
ureadahead-other stop/waiting
apport stop/waiting
console-setup stop/waiting
hwclock-save stop/waiting
irqbalance stop/waiting
plymouth-log stop/waiting
tty5 start/running, process 915
atd start/running, process 939
dbus start/running, process 755
failsafe-x stop/waiting
plymouth stop/waiting
control-alt-delete stop/waiting
hwclock stop/waiting
network-manager start/running, process 773
module-init-tools stop/waiting
cron start/running, process 936
gdm start/running, process 766
mountall stop/waiting
acpid start/running, process 930
plymouth-stop stop/waiting
rcS stop/waiting
ufw start/running
mounted-varrun stop/waiting
rc-sysinit stop/waiting
anacron stop/waiting
tty2 start/running, process 923
udevtrigger stop/waiting
mounted-dev stop/waiting
tty3 start/running, process 924
udev-finish stop/waiting
hostname stop/waiting
mountall-reboot stop/waiting
mysql start/running, process 978
mountall-shell stop/waiting
mounted-tmp stop/waiting
network-interface (lo) start/running
network-interface (eth0) start/running
plymouth-splash stop/waiting
tty1 start/running, process 1171
udevmonitor stop/waiting
dmesg stop/waiting
network-interface-security (network-manager) start/running
network-interface-security (network-interface/eth0) start/running
network-interface-security (network-interface/lo) start/running
network-interface-security (networking) start/running
networking stop/waiting
procps stop/waiting
tty6 start/running, process 927
ureadahead stop/waiting

```

---

### Post by piquat on 2011-01-26
> **erelsgl said:**
> This is what I see after I startup and start Firefox (before I start Firefox, the "used" is about 1400 - less than now but still very high):

```
erelsgl@ubuntu:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          2000       1957         42          0        663        832
**-/+ buffers/cache:        460       _*1539*_**
Swap:          254          0        254

```

Looks like you have 1539MB free/cached.

I'm running a laptop with 2GB of memory right now and that's right about what I get.  That bolded line also seems to agree with System Monitor.

---

### Post by Topsiho on 2011-01-26
As far as I understand, Linux, and Ubuntu, keeps information in memory, even after use, until the memory is needed for other things. This way, if the information is needed again (a program is restarted or so), it is still in memory and ready to be used.
So it's really great that in Linux the available memory is used optimally (that means: all of it.)

If the memory is large enough (I read somewhere) to contain the entire contents of the / partition, then it's possible to load all contents from / into memory when booting, and run from there, after which the computer runs a lot faster then from the hard disk. Only the booting is slowed down some.

So ...

Topsiho

---

### Post by erelsgl on 2011-01-30
Thank you! I just didn't know that the important line is the "+/- buffers/cache" one. Now it all makes sense!

---

### Post by asmoore82 on 2011-01-30
You can use the `pv` command(pipe viewer) to see the amazing cache in action.

Just repeat forcing the read of a large file multiple times and watch the speed!:
```
**$** pv ubuntu-10.04.1-desktop-amd64.iso >/dev/null
 686MB 0:00:11 [61.3MB/s] [=================================>] 100%            
**$** pv ubuntu-10.04.1-desktop-amd64.iso >/dev/null
 686MB 0:00:00 [2.73GB/s] [=================================>] 100%            
**$** pv ubuntu-10.04.1-desktop-amd64.iso >/dev/null
 686MB 0:00:00 [   3GB/s] [=================================>] 100%
```

---


---
title: "YES command starts automatically at startup"
date: 2010-10-12
forum: General Help
---

### Post by orlandod543 on 2010-10-12
Hi Everyone.

Since a few weeks my PC have been working slow and the gnome system Monitor says that my cpu is working at 100% all the time. when I ran top command appears:

 PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
  770 root      20   0  4060  308  240 R   76  0.0   8:41.05 yes                
  919 root      20   0  4060  312  240 R   49  0.0   8:23.39 yes                
  768 root      20   0  4060  308  240 R   49  0.0   7:52.40 yes                
 2007 orlando   20   0  314m 100m  18m S   11  5.0   1:19.75 npviewer.bin       
  900 root      15  -5     0    0    0 S    4  0.0   0:04.69 kslowd001          
 1095 root      20   0  131m  25m  11m S    3  1.3   0:23.95 Xorg               
 1961 orlando   20   0  713m 130m  32m S    3  6.5   0:45.41 firefox-bin        
 1763 orlando    9 -11  337m 6864 5064 S    2  0.3   0:14.51 pulseaudio         
 2194 orlando   20   0  244m  17m  11m S    2  0.9   0:00.97 gnome-terminal     
 2061 orlando   30  10  343m  64m  34m R    1  3.2   0:08.17 update-manager     
   10 root      20   0     0    0    0 S    0  0.0   0:00.20 events/1           
   85 root      20   0     0    0    0 S    0  0.0   0:00.32 kondemand/1        
 1931 orlando   20   0  224m  13m  10m S    0  0.7   0:00.68 update-notifier    
 2312 root      20   0 19384 1376  948 R    0  0.1   0:00.41 top                
    1 root      20   0 23900 2060 1296 S    0  0.1   0:00.51 init               
    2 root      20   0     0    0    0 S    0  0.0   0:00.00


That "yes" command is consuming all my cpu, and everytime I startup I have to kill it manually.

I've found that running in a terminal the "yes" command makes that appears continuously a "Y" character.
Anybody Knows how to Solve it?

I'm running Ubuntu 10.10 64bit

Thank You.

---

### Post by gzarkadas on 2010-10-13
Execute, before killing the `yes' processes, in a terminal the following command to locate the parent processes that spawn `yes':

```

sudo ps -AHf | less

```To quickly locate yes, type inside less window: `/\/usr\/bin\/yes' and press `<Enter>'. Then press `n' to go to next occurrence.

For each occurrence found, scroll the less window up to find the top-most process (below /sbin/init, since all processes ultimately start by init; this means you stop when there are three spaces after the time column). Note it down.

Then find the startup script or service that resulted in yes launched and try to figure out where the corresponding script error is.

---

### Post by cgroza on 2010-10-13
Did you added any scripts lately? Because from here it seems you are the victim of a prank.

---

### Post by k7k0 on 2011-03-25
I'm having this problem right now in one of my servers.
There's always three 'yes' commands running and consuming cpu. Any ideas how to troubleshoot this? thanks

---

### Post by k7k0 on 2011-03-25
Here's the output of ps -AHf

```

UID        PID  PPID  C STIME TTY          TIME CMD
root         2     0  0 17:33 ?        00:00:00 [kthreadd]
root         3     2  0 17:33 ?        00:00:00   [migration/0]
root         4     2  0 17:33 ?        00:00:00   [ksoftirqd/0]
root         5     2  0 17:33 ?        00:00:00   [watchdog/0]
root         6     2  0 17:33 ?        00:00:00   [migration/1]
root         7     2  0 17:33 ?        00:00:00   [ksoftirqd/1]
root         8     2  0 17:33 ?        00:00:00   [watchdog/1]
root         9     2  0 17:33 ?        00:00:00   [migration/2]
root        10     2  0 17:33 ?        00:00:00   [ksoftirqd/2]
root        11     2  0 17:33 ?        00:00:00   [watchdog/2]
root        12     2  0 17:33 ?        00:00:00   [migration/3]
root        13     2  0 17:33 ?        00:00:00   [ksoftirqd/3]
root        14     2  0 17:33 ?        00:00:00   [watchdog/3]
root        15     2  0 17:33 ?        00:00:00   [migration/4]
root        16     2  0 17:33 ?        00:00:00   [ksoftirqd/4]
root        17     2  0 17:33 ?        00:00:00   [watchdog/4]
root        18     2  0 17:33 ?        00:00:00   [migration/5]
root        19     2  0 17:33 ?        00:00:00   [ksoftirqd/5]
root        20     2  0 17:33 ?        00:00:00   [watchdog/5]
root        21     2  0 17:33 ?        00:00:00   [migration/6]
root        22     2  0 17:33 ?        00:00:00   [ksoftirqd/6]
root        23     2  0 17:33 ?        00:00:00   [watchdog/6]
root        24     2  0 17:33 ?        00:00:00   [migration/7]
root        25     2  0 17:33 ?        00:00:00   [ksoftirqd/7]
root        26     2  0 17:33 ?        00:00:00   [watchdog/7]
root        27     2  0 17:33 ?        00:00:00   [events/0]
root        28     2  0 17:33 ?        00:00:00   [events/1]
root        29     2  0 17:33 ?        00:00:00   [events/2]
root        30     2  0 17:33 ?        00:00:00   [events/3]
root        31     2  0 17:33 ?        00:00:00   [events/4]
root        32     2  0 17:33 ?        00:00:00   [events/5]
root        33     2  0 17:33 ?        00:00:00   [events/6]
root        34     2  0 17:33 ?        00:00:00   [events/7]
root        35     2  0 17:33 ?        00:00:00   [cpuset]
root        36     2  0 17:33 ?        00:00:00   [khelper]
root        37     2  0 17:33 ?        00:00:00   [netns]
root        38     2  0 17:33 ?        00:00:00   [async/mgr]
root        39     2  0 17:33 ?        00:00:00   [pm]
root        41     2  0 17:33 ?        00:00:00   [sync_supers]
root        42     2  0 17:33 ?        00:00:00   [bdi-default]
root        43     2  0 17:33 ?        00:00:00   [kintegrityd/0]
root        44     2  0 17:33 ?        00:00:00   [kintegrityd/1]
root        45     2  0 17:33 ?        00:00:00   [kintegrityd/2]
root        46     2  0 17:33 ?        00:00:00   [kintegrityd/3]
root        47     2  0 17:33 ?        00:00:00   [kintegrityd/4]
root        48     2  0 17:33 ?        00:00:00   [kintegrityd/5]
root        49     2  0 17:33 ?        00:00:00   [kintegrityd/6]
root        50     2  0 17:33 ?        00:00:00   [kintegrityd/7]
root        51     2  0 17:33 ?        00:00:00   [kblockd/0]
root        52     2  0 17:33 ?        00:00:00   [kblockd/1]
root        53     2  0 17:33 ?        00:00:00   [kblockd/2]
root        54     2  0 17:33 ?        00:00:00   [kblockd/3]
root        55     2  0 17:33 ?        00:00:00   [kblockd/4]
root        56     2  0 17:33 ?        00:00:00   [kblockd/5]
root        57     2  0 17:33 ?        00:00:00   [kblockd/6]
root        58     2  0 17:33 ?        00:00:00   [kblockd/7]
root        59     2  0 17:33 ?        00:00:00   [kacpid]
root        60     2  0 17:33 ?        00:00:00   [kacpi_notify]
root        61     2  0 17:33 ?        00:00:00   [kacpi_hotplug]
root        62     2  0 17:33 ?        00:00:00   [ata/0]
root        63     2  0 17:33 ?        00:00:00   [ata/1]
root        64     2  0 17:33 ?        00:00:00   [ata/2]
root        65     2  0 17:33 ?        00:00:00   [ata/3]
root        66     2  0 17:33 ?        00:00:00   [ata/4]
root        67     2  0 17:33 ?        00:00:00   [ata/5]
root        68     2  0 17:33 ?        00:00:00   [ata/6]
root        69     2  0 17:33 ?        00:00:00   [ata/7]
root        70     2  0 17:33 ?        00:00:00   [ata_aux]
root        71     2  0 17:33 ?        00:00:00   [ksuspend_usbd]
root        72     2  0 17:33 ?        00:00:00   [khubd]
root        73     2  0 17:33 ?        00:00:00   [kseriod]
root        74     2  0 17:33 ?        00:00:00   [kmmcd]
root        83     2  0 17:33 ?        00:00:00   [khungtaskd]
root        84     2  0 17:33 ?        00:00:00   [kswapd0]
root        85     2  0 17:33 ?        00:00:00   [ksmd]
root        86     2  0 17:33 ?        00:00:00   [aio/0]
root        87     2  0 17:33 ?        00:00:00   [aio/1]
root        88     2  0 17:33 ?        00:00:00   [aio/2]
root        89     2  0 17:33 ?        00:00:00   [aio/3]
root        90     2  0 17:33 ?        00:00:00   [aio/4]
root        91     2  0 17:33 ?        00:00:00   [aio/5]
root        92     2  0 17:33 ?        00:00:00   [aio/6]
root        93     2  0 17:33 ?        00:00:00   [aio/7]
root        94     2  0 17:33 ?        00:00:00   [ecryptfs-kthrea]
root        95     2  0 17:33 ?        00:00:00   [crypto/0]
root        96     2  0 17:33 ?        00:00:00   [crypto/1]
root        97     2  0 17:33 ?        00:00:00   [crypto/2]
root        98     2  0 17:33 ?        00:00:00   [crypto/3]
root        99     2  0 17:33 ?        00:00:00   [crypto/4]
root       100     2  0 17:33 ?        00:00:00   [crypto/5]
root       101     2  0 17:33 ?        00:00:00   [crypto/6]
root       102     2  0 17:33 ?        00:00:00   [crypto/7]
root       121     2  0 17:33 ?        00:00:00   [scsi_eh_0]
root       122     2  0 17:33 ?        00:00:00   [scsi_eh_1]
root       123     2  0 17:33 ?        00:00:00   [scsi_eh_2]
root       126     2  0 17:33 ?        00:00:00   [scsi_eh_3]
root       129     2  0 17:33 ?        00:00:00   [kstriped]
root       130     2  0 17:33 ?        00:00:00   [kmpathd/0]
root       131     2  0 17:33 ?        00:00:00   [kmpathd/1]
root       132     2  0 17:33 ?        00:00:00   [kmpathd/2]
root       133     2  0 17:33 ?        00:00:00   [kmpathd/3]
root       134     2  0 17:33 ?        00:00:00   [kmpathd/4]
root       135     2  0 17:33 ?        00:00:00   [kmpathd/5]
root       136     2  0 17:33 ?        00:00:00   [kmpathd/6]
root       137     2  0 17:33 ?        00:00:00   [kmpathd/7]
root       138     2  0 17:33 ?        00:00:00   [kmpath_handlerd]
root       139     2  0 17:33 ?        00:00:00   [ksnapd]
root       140     2  0 17:33 ?        00:00:00   [kondemand/0]
root       141     2  0 17:33 ?        00:00:00   [kondemand/1]
root       142     2  0 17:33 ?        00:00:00   [kondemand/2]
root       143     2  0 17:33 ?        00:00:00   [kondemand/3]
root       144     2  0 17:33 ?        00:00:00   [kondemand/4]
root       145     2  0 17:33 ?        00:00:00   [kondemand/5]
root       146     2  0 17:33 ?        00:00:00   [kondemand/6]
root       147     2  0 17:33 ?        00:00:00   [kondemand/7]
root       148     2  0 17:33 ?        00:00:00   [kconservative/0]
root       149     2  0 17:33 ?        00:00:00   [kconservative/1]
root       150     2  0 17:33 ?        00:00:00   [kconservative/2]
root       151     2  0 17:33 ?        00:00:00   [kconservative/3]
root       152     2  0 17:33 ?        00:00:00   [kconservative/4]
root       153     2  0 17:33 ?        00:00:00   [kconservative/5]
root       154     2  0 17:33 ?        00:00:00   [kconservative/6]
root       155     2  0 17:33 ?        00:00:00   [kconservative/7]
root       284     2  0 17:33 ?        00:00:00   [scsi_eh_4]
root       386     2  0 17:33 ?        00:00:00   [flush-1:0]
root       387     2  0 17:33 ?        00:00:00   [flush-1:1]
root       389     2  0 17:33 ?        00:00:00   [flush-1:3]
root       391     2  0 17:33 ?        00:00:00   [flush-1:5]
root       393     2  0 17:33 ?        00:00:00   [flush-1:7]
root       394     2  0 17:33 ?        00:00:00   [flush-1:8]
root       395     2  0 17:33 ?        00:00:00   [flush-1:9]
root       396     2  0 17:33 ?        00:00:00   [flush-1:10]
root       397     2  0 17:33 ?        00:00:00   [flush-1:11]
root       398     2  0 17:33 ?        00:00:00   [flush-1:12]
root       399     2  0 17:33 ?        00:00:00   [flush-1:13]
root       400     2  0 17:33 ?        00:00:00   [flush-1:14]
root       402     2  0 17:33 ?        00:00:00   [flush-8:0]
root       405     2  0 17:33 ?        00:00:00   [kjournald]
root       707     2  0 17:33 ?        00:00:00   [kpsmoused]
root         1     0  0 17:33 ?        00:00:01 /sbin/init
root       734     1 99 17:33 ?        00:04:56   yes
root      1032     1  0 17:33 ?        00:00:00   /bin/sh -e /proc/self/fd/10
root      1034  1032 99 17:33 ?        00:04:55     yes
root      1033     1  0 17:33 ?        00:00:00   /bin/sh -e /proc/self/fd/10
root      1035  1033 99 17:33 ?        00:04:55     yes
root      1174     1  0 17:33 ?        00:00:00   /usr/sbin/sshd -D
root      1482  1174  0 17:33 ?        00:00:00     sshd: smarconi [priv]
smarconi  1556  1482  0 17:33 ?        00:00:00       sshd: smarconi@pts/0
smarconi  1557  1556  0 17:33 pts/0    00:00:00         -bash
root      1695  1557  0 17:33 pts/0    00:00:00           -bash
root      1934  1695  0 17:38 pts/0    00:00:00             ps -AHf
root      1211     1  0 17:33 tty4     00:00:00   /sbin/getty -8 38400 tty4
root      1215     1  0 17:33 tty5     00:00:00   /sbin/getty -8 38400 tty5
root      1219     1  0 17:33 tty2     00:00:00   /sbin/getty -8 38400 tty2
root      1220     1  0 17:33 tty3     00:00:00   /sbin/getty -8 38400 tty3
root      1222     1  0 17:33 tty6     00:00:00   /sbin/getty -8 38400 tty6
root      1234     1  0 17:33 ?        00:00:00   /usr/sbin/irqbalance
root      1464     1  0 17:33 tty1     00:00:00   /sbin/getty -8 38400 tty1
root      1875     1  0 17:35 ?        00:00:00   /bin/sh -e /proc/self/fd/10
root      1877  1875 99 17:35 ?        00:02:49     yes


```

How can this processes start?

---

### Post by k7k0 on 2011-03-25
Figured out. There was an error in /etc/default/nfs-common

instead of adding
NEED_IDMAPD=yes

I've added
NEED_IDMAPD= yes

The extra space caused the execution of the command :(

---

### Post by vistor on 2011-10-02
perfect, thanks for this, got really confused there for a sec.
Had the same NFS-issue.

:popcorn:

---


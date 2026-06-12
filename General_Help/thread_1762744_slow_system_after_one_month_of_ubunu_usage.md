---
title: "slow system after one month of ubunu usage"
date: 2011-05-19
forum: General Help
---

### Post by goshalram on 2011-05-19
**i installed ubuntu 11.04 beta rarely two months before. i m updating the  version regularly. my system seems to slow very much for merely a month  after its installation.what shall i do?**

---

### Post by tygern on 2011-05-19
What do you get when you type "ps aux" into the terminal?

---

### Post by r-senior on 2011-05-19
Have you looked in your log files to see if there are any repetitive messages?

/var/log/syslog
/var/log/dmesg
~/.xsession-errors

What are the specifications of the machine? CPU/Memory/Graphics Card?

How about running top?

---

### Post by goshalram on 2011-05-19
**s i get a long list of codes with ps aux in the last line. bash in the last but one line and so on**

---

### Post by tygern on 2011-05-19
> **goshalram said:**
> **s i get a long list of codes with ps aux in the last line. bash in the last but one line and so on**

Will you please paste the output that you get from ps aux?

---

### Post by goshalram on 2011-05-19
disks
goshal    1453  0.0  1.8  73592 55300 ?        Sl   May19   0:02 /usr/bin/python
goshal    1455  0.0  0.4  78584 12112 ?        Sl   May19   0:00 /usr/lib/notify
root      1456  0.0  0.0   5564   716 ?        S    May19   0:00 udisks-daemon: 
goshal    1459  0.0  0.0  18204  2248 ?        Sl   May19   0:00 /usr/lib/gvfs/g
goshal    1464  0.0  0.0   8512  2280 ?        S    May19   0:00 /usr/lib/gvfs/g
goshal    1466  0.0  0.0   8424  1548 ?        S    May19   0:00 /usr/bin/gnome-
goshal    1473  0.1  0.1  17804  3732 ?        S    May19   0:03 /usr/lib/gvfs/g
goshal    1474  0.0  0.0  28052  2856 ?        Ss   May19   0:00 gnome-screensav
root      1475  0.0  0.0   2552  1256 ?        S    May19   0:00 /sbin/dhclient
goshal    1476  0.0  0.0   3912   248 ?        S    May19   0:00 /bin/cat
goshal    1478  0.0  0.2  19356  6280 ?        S    May19   0:00 /usr/lib/gnome-
goshal    1484  0.0  0.0   7764  2504 ?        S    May19   0:00 /usr/lib/gvfs/g
goshal    1498  0.0  0.2  52420  8320 ?        Sl   May19   0:02 zeitgeist-datah
goshal    1546  0.0  0.0  22520  2412 ?        Sl   May19   0:00 /usr/lib/d-conf
goshal    1558  0.0  0.0   1912   508 ?        Ss   May19   0:00 /bin/sh -c /usr
goshal    1559  0.0  0.3  29916 10400 ?        Sl   May19   0:00 /usr/bin/unity-
goshal    1561  0.0  0.2  65884  8168 ?        S    May19   0:00 /usr/lib/bamf/b
goshal    1566  5.1  1.5 136872 45732 ?        Sl   May19   2:33 /usr/lib/unity/
goshal    1576  0.0  0.0   7740  2268 ?        S    May19   0:00 /usr/lib/gvfs/g
goshal    1590  0.0  0.2  55672  6752 ?        Sl   May19   0:00 /usr/lib/unity-
goshal    1592  0.0  0.1  51076  4264 ?        Sl   May19   0:00 /usr/lib/unity-
goshal    1629  0.0  0.1  61096  4916 ?        Sl   May19   0:00 /usr/lib/indica
goshal    1631  0.0  0.1  40500  4132 ?        Sl   May19   0:00 /usr/lib/indica
goshal    1633  0.0  0.1 128300  5284 ?        Sl   May19   0:00 /usr/lib/indica
goshal    1635  0.0  0.1  50784  5224 ?        Sl   May19   0:00 /usr/lib/indica
goshal    1637  0.0  0.1  51112  4368 ?        Sl   May19   0:00 /usr/lib/indica
goshal    1639  0.0  0.2  58804  6736 ?        Sl   May19   0:00 /usr/lib/indica
goshal    1666  0.0  0.1  19088  4128 ?        Sl   May19   0:00 /usr/lib/geoclu
goshal    1835  9.3  5.0 522136 151448 ?       Sl   May19   4:30 /usr/lib/firefo
root      1931  0.0  0.0   2872  1140 ?        S<   May19   0:00 udevd --daemon
root      2290  0.0  0.0      0     0 ?        S    May19   0:00 [kworker/u:0]
goshal    2298  1.0  0.8 102080 24620 ?        Sl   May19   0:23 /usr/lib/firefo
root      2365  0.0  0.0      0     0 ?        S    00:10   0:00 [kworker/0:1]
root      2368  0.0  0.0      0     0 ?        S    00:11   0:00 [kworker/1:1]
root      2383  0.0  0.0      0     0 ?        S    00:15   0:00 [kworker/0:2]
root      2388  0.0  0.0      0     0 ?        S    00:17   0:00 [kworker/1:0]
root      2392  0.0  0.0      0     0 ?        S    00:18   0:00 [kworker/u:1]
root      2393  0.0  0.0      0     0 ?        S    00:21   0:00 [kworker/0:0]
root      2395  0.0  0.0      0     0 ?        S    00:22   0:00 [kworker/1:2]
goshal    2402  1.4  0.4  96760 13820 ?        Sl   00:23   0:00 gnome-terminal
goshal    2407  0.0  0.0   2068   712 ?        S    00:23   0:00 gnome-pty-helpe
goshal    2408  2.0  0.1   6948  3564 pts/0    Ss   00:23   0:00 bash
goshal    2461  0.0  0.0   4708  1196 pts/0    R+   00:24   0:00 ps aux

---

### Post by goshalram on 2011-05-19
My system specification is 4gb ram, 320 gb hard disk, core to duo ,no grafic card

---

### Post by tygern on 2011-05-19
What percentage of your CPU is being used when you run top?

---

### Post by goshalram on 2011-05-19
How to find that sir

---

### Post by StrayEddy on 2011-05-19
Go to *System->Administration->System Monitor*
 
There choose tab *Resources*
 
You should see the CPU usage then.

---

### Post by goshalram on 2011-05-19
There i get cpu1 usage about 7% , cpu2 usage 8%

---

### Post by StrayEddy on 2011-05-19
Sorry can t help. Someone. **Bump**

---

### Post by r-senior on 2011-05-19
Is it slow all the time. Or only sometimes?

Is it that programs are slow to start?

Does your hard disk make lots of noise and the disk LED flash a lot?

Is it graphics that's slow, moving windows around, etc.

Could you go into a terminal and post the output of these commands?

```

free
top -n1
df -h

```

---

### Post by StrayEddy on 2011-05-19
To go into a terminal:
 
Ctrl+Alt+T

---


---
title: "Swap Loader Not Found"
date: 2012-01-02
forum: General Help
---

### Post by linux_noobq2m on 2012-01-02
Hello

I am a first time user so please try to ignore my lack of technical knowledge.

I am using Ubuntu through Wubi. My version is 11.10.

So, whenever I suspended and restarted ubuntu, it used to go to a non-GUI mode for a few seconds, show "Low swap memory" and go back to normal without anything happening (all of the programs that were on before suspending were still on).

Searching, I found the solution [here]("https://wiki.ubuntu.com/WubiGuide#How_do_I_increase_my_swap_space.3F") on how to increase swap disk size. However, when I increased the swap size as shown there, suspended and restarted (after rebooting), it again went to non-GUI mode and showed error "Swap Loader Not Found" and came to normal, without closing any programs.

Now, I have deleted the swap.disk and renamed the swap.disk.bak to swap.disk

Does anyone know what the problem is? Thanks in advance :D

---

### Post by Synoc on 2012-01-02
try typing ```
swapon
``` just to make sure it's on, it probably won't help but it might give us an error message. also in terminal type ```
ls /proc
``` and post the output here. After you paste the output, highlight and select the "#" button to place that text into a code window so it preserves everything. 

this might help us get an idea what to do next in the meantime I'd suggest disabling hibernate.

---

### Post by Frogs Hair on 2012-01-02
As you know Wubi only sets aside 250 Mb of swap by default although suspend / sleep is possible , it is not set up to hibernate . I don't know if simply increasing swap space alone will allow you to hibernate .

---

### Post by linux_noobq2m on 2012-01-02
@Synoc

Here is the output you asked for:
command: swapon

```
Usage:
 swapon -a [-e] [-v] [-f]             enable all swaps from /etc/fstab
 swapon [-p priority] [-d] [-v] [-f] <special>  enable given swap
 swapon -s                            display swap usage summary
 swapon -h                            display help
 swapon -V                            display version

The <special> parameter:
 {-L label | LABEL=label}             LABEL of device to be used
 {-U uuid  | UUID=uuid}               UUID of device to be used
 <device>                             name of device to be used
 <file>                               name of file to be used

```

command: ls /proc

```
1     1346  1427  16    24   816  975          ioports        self
10    1351  1443  1642  25   819  978          irq            slabinfo
1030  1352  1445  1685  251  820  acpi         kallsyms       softirqs
1031  1354  1447  17    259  821  asound       kcore          stat
11    1358  1450  1705  26   824  buddyinfo    key-users      swaps
1101  1360  1453  1716  260  860  bus          kmsg           sys
1108  1365  1458  1755  3    865  cgroups      kpagecount     sysrq-trigger
1111  1366  1488  1761  323  874  cmdline      kpageflags     sysvipc
1184  1367  1491  1765  328  875  consoles     latency_stats  timer_list
12    1368  1493  1789  34   878  cpuinfo      loadavg        timer_stats
1221  1369  1496  1797  35   880  crypto       locks          tty
1224  1371  1498  1798  4    883  devices      mdstat         uptime
1225  1375  15    18    456  884  device-tree  meminfo        version
1227  1381  1500  1852  457  885  diskstats    misc           version_signature
1232  1389  1501  196   5    887  dma          modules        vmallocinfo
1243  1391  1507  2     524  889  dri          mounts         vmstat
1246  1392  1508  20    6    892  driver       mtrr           zoneinfo
1256  14    1517  201   648  9    execdomains  net
13    1400  1520  21    695  928  fb           pagetypeinfo
1327  1403  1572  22    7    936  filesystems  partitions
1338  1421  1578  227   780  956  fs           sched_debug
1343  1424  1580  228   8    957  interrupts   schedstat
1345  1425  1582  23    807  970  iomem        scsi

```

Hope this helps!

@Frogs Hair

> **Frogs Hair said:**
> I don't know if simply increasing swap space alone will allow you to hibernate .

Then, how can I hibernate?

---

### Post by oldos2er on 2012-01-02
Wubi doesn't support hibernation. [https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

You'll need to install Ubuntu to its own partition with a suitably sized swap partition to hibernate.

---


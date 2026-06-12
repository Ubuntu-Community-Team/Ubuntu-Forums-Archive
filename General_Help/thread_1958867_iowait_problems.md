---
title: "iowait problems"
date: 2012-04-15
forum: General Help
---

### Post by SiN486 on 2012-04-15
Recently my ubuntu 10.04.4 install has been 'freezing' at randomly for minutes at a time. It happens when opening any application (terminal, gedit, vlc, etc) and my boot time has also shot up.

What I think is happening is when I load an application for the first time, the files required are read from disk, and this takes a LONG time. But after this, it is in memory and responsiveness is as expected.

[Here is a bootchart from today]("http://imageshack.us/photo/my-images/694/what9000lucid201204151.png/") (warning large image). You can see that it takes 500 seconds to boot. I've disabled ureadahead, and it actually helped for a couple of boots, but now it takes ages again.

I ran 'sar 5 100' and then I loaded a webpage remotely (I have apache running on this ubuntu installation), I only loaded a static html file.

```

sinaptik@what9000:~$ sar 5 100
Linux 2.6.32-40-generic-pae (what9000) 	15/04/12 	_i686_	(2 CPU)

18:13:20        CPU     %user     %nice   %system   %iowait    %steal     %idle
18:13:25        all      5.03      0.00      1.09      0.00      0.00     93.88
18:13:30        all      2.59      0.00      0.40      0.00      0.00     97.01
18:13:35        all      3.07      0.00      0.79      0.00      0.00     96.14
18:13:40        all      3.97      0.00      0.89      0.00      0.00     95.13
18:13:45        all      2.66      0.00      0.98      0.00      0.00     96.36
18:13:50        all      2.96      0.00      0.59      0.00      0.00     96.45
18:13:55        all      8.49      0.00      2.03      8.39      0.00     81.10
18:14:00        all      7.82      0.00      3.24     23.45      0.00     65.49
18:14:05        all      9.81      0.00      2.76     48.19      0.00     39.24
18:14:10        all      7.43      0.00      3.33     49.62      0.00     39.62
18:14:15        all      8.02      0.00      3.05     56.77      0.00     32.16
18:14:20        all      5.19      0.00      2.02     83.19      0.00      9.61
18:14:25        all      7.19      0.00      2.01     59.64      0.00     31.16
18:14:30        all      3.98      0.00      1.55     84.55      0.00      9.91
18:14:35        all      6.01      0.00      1.94     85.56      0.00      6.49
18:14:40        all      5.30      0.00      0.98     93.71      0.00      0.00
18:14:45        all      3.83      0.00      1.08     95.09      0.00      0.00
18:14:50        all      3.63      0.00      1.28     68.01      0.00     27.09
18:14:55        all      3.83      0.00      1.08     65.88      0.00     29.20
18:15:00        all      4.02      0.00      0.59     47.75      0.00     47.65
18:15:05        all      3.64      0.00      1.18     79.65      0.00     15.54
18:15:10        all      3.75      0.00      0.79     95.36      0.00      0.10

18:15:10        CPU     %user     %nice   %system   %iowait    %steal     %idle
18:15:15        all      3.25      0.00      0.99     95.76      0.00      0.00
18:15:20        all      3.35      0.00      0.59     96.06      0.00      0.00
18:15:25        all      3.34      0.00      1.08     95.48      0.00      0.10
18:15:30        all      3.06      0.00      0.69     96.25      0.00      0.00
18:15:35        all      3.82      0.00      1.08     95.10      0.00      0.00
18:15:40        all      3.25      0.00      0.59     96.15      0.00      0.00
18:15:45        all      3.72      0.00      0.88     95.40      0.00      0.00
18:15:50        all      3.06      0.00      0.99     95.95      0.00      0.00
18:15:55        all      3.15      0.00      0.89     95.96      0.00      0.00
18:16:00        all      2.96      0.00      0.59     96.45      0.00      0.00
18:16:05        all      8.07      0.00      1.87     89.96      0.00      0.10
18:16:10        all      3.26      0.00      0.49     96.25      0.00      0.00
18:16:15        all      3.47      0.00      0.79     95.74      0.00      0.00
18:16:20        all      2.87      0.00      0.40     96.73      0.00      0.00
18:16:25        all      7.72      0.00      1.88     90.30      0.00      0.10
18:16:30        all      2.68      0.00      0.60     96.72      0.00      0.00
18:16:35        all      3.07      0.00      0.69     96.24      0.00      0.00
18:16:40        all      3.06      0.00      0.59     96.35      0.00      0.00
18:16:45        all      1.88      0.00      0.50     97.62      0.00      0.00
18:16:50        all      3.37      0.00      0.40     96.23      0.00      0.00
18:16:55        all      5.82      0.00      1.08     93.10      0.00      0.00
18:17:00        all      2.57      0.00      0.79     96.64      0.00      0.00

18:17:00        CPU     %user     %nice   %system   %iowait    %steal     %idle
18:17:05        all      4.16      0.00      0.79     59.90      0.00     35.15
18:17:10        all      3.88      0.00      0.70     95.42      0.00      0.00
18:17:15        all      2.88      0.00      0.89     96.22      0.00      0.00
18:17:20        all      2.79      0.00      0.30     96.92      0.00      0.00
18:17:25        all      4.04      0.00      0.89     95.07      0.00      0.00
18:17:30        all      2.59      0.00      0.50     58.38      0.00     38.52
18:17:35        all      5.92      0.00      1.08     47.53      0.00     45.46
18:17:40        all      4.06      0.00      0.49     67.95      0.00     27.50
18:17:45        all      3.17      0.00      0.50     96.23      0.00      0.10
18:17:50        all      3.08      0.00      0.40     96.53      0.00      0.00
18:17:55        all      2.87      0.00      0.69     80.04      0.00     16.40
18:18:00        all      5.37      0.00      1.19     64.81      0.00     28.63
18:18:05        all      2.88      0.00      0.79     70.80      0.00     25.52
18:18:10        all     14.61      0.00      4.24     67.03      0.00     14.12
18:18:15        all      4.02      0.00      1.18      1.37      0.00     93.42
18:18:20        all      3.93      0.00      0.79     22.47      0.00     72.82
18:18:25        all      5.65      0.00      0.89     93.45      0.00      0.00
18:18:30        all      3.84      0.00      1.08     75.10      0.00     19.98
18:18:35        all      3.56      0.00      0.99     47.68      0.00     47.77
18:18:40        all      4.74      0.00      0.59     48.42      0.00     46.25
18:18:45        all      3.71      0.00      0.98     31.87      0.00     63.44
18:18:50        all      3.28      0.00      0.70      0.20      0.00     95.83

18:18:50        CPU     %user     %nice   %system   %iowait    %steal     %idle
18:18:55        all      6.54      0.00      1.17     16.89      0.00     75.39
18:19:00        all      6.39      0.00      1.18     18.78      0.00     73.65
18:19:05        all      4.82      0.00      1.38     21.83      0.00     71.98
18:19:10        all      4.25      0.00      0.99      0.10      0.00     94.66
18:19:15        all      2.66      0.00      0.59      0.00      0.00     96.75
18:19:20        all      3.74      0.00      0.89      0.00      0.00     95.37
18:19:25        all      6.31      0.00      1.28      1.08      0.00     91.32


```

It takes a whole five minutes for the page to load.

Is there anything I can do to fix this? Having my computer freeze for five minutes at a time is insanely frustrating.

Thanks.

---

### Post by dcstar on 2012-04-15
> **SiN486 said:**
> Recently my ubuntu 10.04.4 install has been 'freezing' at randomly for minutes at a time. It happens when opening any application (terminal, gedit, vlc, etc) and my boot time has also shot up.
..........
Is there anything I can do to fix this? Having my computer freeze for five minutes at a time is insanely frustrating.

Thanks.

Check for bad blocks on your drive and replace it ASAP if there are any.

---

### Post by SiN486 on 2012-04-16
> **dcstar said:**
> Check for bad blocks on your drive and replace it ASAP if there are any.

```
Checking for bad blocks (read-only test): done
Pass completed, 0 bad blocks found.
```

No bad blocks on any partitions. What else could be the cause?

---


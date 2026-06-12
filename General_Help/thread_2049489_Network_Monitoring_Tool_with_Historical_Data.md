---
title: "Network Monitoring Tool with Historical Data?"
date: 2012-08-28
forum: General Help
---

### Post by matimont on 2012-08-28
Hi,

Is there a good network monitoring tool that would collect historical statistics like total bytes in and out? I tried cacti but I wasn't able to make it work for network..

I'm using Ubuntu 12.04 Server on my VPS.

Thank you!

---

### Post by GreatDanton on 2012-08-28
Wireshark?

Regards.

---

### Post by Cheesemill on 2012-08-28
I use vnstat, you can use it to show daily, weekly and monthly stats as well as much more:
```
rob@arch:~$ vnstat -d

 eth0  /  daily

         day         rx      |     tx      |    total    |   avg. rate
     ------------------------+-------------+-------------+---------------
      08/05/12      1.81 GiB |   55.02 MiB |    1.87 GiB |  181.13 kbit/s
      08/06/12    863.12 MiB |   41.05 MiB |  904.17 MiB |   85.73 kbit/s
      08/07/12      2.24 GiB |  536.85 MiB |    2.76 GiB |  268.21 kbit/s
      08/08/12    758.86 MiB |  792.31 MiB |    1.51 GiB |  147.07 kbit/s
      08/09/12      1.67 GiB |    1.69 GiB |    3.37 GiB |  327.08 kbit/s
      08/10/12    813.68 MiB |  470.68 MiB |    1.25 GiB |  121.78 kbit/s
      08/11/12    878.93 MiB |  896.72 MiB |    1.73 GiB |  168.36 kbit/s
      08/12/12      4.14 GiB |    1.89 GiB |    6.03 GiB |  585.87 kbit/s
      08/13/12      1.53 GiB |    1.26 GiB |    2.78 GiB |  270.28 kbit/s
      08/14/12    492.59 MiB |  300.86 MiB |  793.45 MiB |   75.23 kbit/s
      08/15/12      8.78 MiB |    8.79 MiB |   17.57 MiB |    1.67 kbit/s
      08/21/12      5.30 GiB |  685.37 MiB |    5.97 GiB |  579.39 kbit/s
      08/22/12      2.06 GiB |    0.99 GiB |    3.05 GiB |  296.12 kbit/s
      08/23/12      6.86 GiB |  305.70 MiB |    7.16 GiB |  694.98 kbit/s
      08/24/12      8.99 GiB |    1.43 GiB |   10.42 GiB |    1.01 Mbit/s
      08/25/12      3.89 GiB |    1.46 GiB |    5.35 GiB |  519.78 kbit/s
      08/26/12      1.98 GiB |    1.08 GiB |    3.06 GiB |  297.20 kbit/s
      08/27/12      4.10 GiB |  586.05 MiB |    4.67 GiB |  453.78 kbit/s
      08/28/12      9.72 GiB |    1.75 GiB |   11.46 GiB |    1.21 Mbit/s
     ------------------------+-------------+-------------+---------------
     estimated     10.55 GiB |    1.89 GiB |   12.44 GiB |
rob@arch:~$ 
rob@arch:~$ 
rob@arch:~$ vnstat -w

 eth0  /  weekly

                      rx      |     tx      |    total    |   avg. rate
   ---------------------------+-------------+-------------+---------------
    last 7 days     37.60 GiB |    7.58 GiB |   45.18 GiB |  633.74 kbit/s
      last week     29.08 GiB |    5.93 GiB |   35.01 GiB |  485.61 kbit/s
   current week     13.82 GiB |    2.32 GiB |   16.13 GiB |  815.27 kbit/s
   ---------------------------+-------------+-------------+---------------
      estimated     50.46 GiB |    8.46 GiB |   58.92 GiB |
rob@arch:~$ 
rob@arch:~$ 
rob@arch:~$ vnstat -m

 eth0  /  monthly

       month        rx      |     tx      |    total    |   avg. rate
    ------------------------+-------------+-------------+---------------
      Aug '12     58.01 GiB |   16.13 GiB |   74.14 GiB |  257.80 kbit/s
    ------------------------+-------------+-------------+---------------
    estimated     64.41 GiB |   17.90 GiB |   82.31 GiB |
```
(my monthly stats are a bit lacking, I reinstalled my OS earlier this month).

---

### Post by matimont on 2012-08-28
I love you man. Works like a charm!

---


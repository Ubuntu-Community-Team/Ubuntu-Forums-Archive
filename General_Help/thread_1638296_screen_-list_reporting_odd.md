---
title: "screen -list reporting odd"
date: 2010-12-05
forum: General Help
---

### Post by renegadeandy on 2010-12-05
Hi!

I wrote a sh script to automate starting a server :

```

#!/bin/bash
echo "Starting CSS in Screen"
cd /home/andy/srcds/orangebox
screen -A -m -d -S csds ./srcds_run -game cstrike -autoupdate +map de_dust
screen -r csds
echo "Started CSS"


```

The server starts - however when i do screen -list - i get:

andy@ubuntu:~$ screen -list
No Sockets found in /var/run/screen/S-andy.

but when i do a ps -aux it shows my server running!?

Please help!

```

root       971  0.0  0.3  19548  3036 ?        Sl   12:51   0:00 /usr/sbin/conso
root      1153  0.0  0.1   4476  1268 ?        Ss   12:52   0:00 SCREEN -A -m -d
root      1155  0.0  0.0   1828   596 pts/1    Ss+  12:52   0:00 /bin/sh ./srcds
root      1346  0.0  0.1   4476  1120 ?        Ss   13:00   0:00 SCREEN -A -m -d
root      1348  0.0  0.0   1828   560 pts/2    Ss+  13:00   0:00 /bin/sh ./srcds
root      1352 45.2 12.3 197004 95028 pts/2    Rl+  13:00 159:39 ./srcds_linux -
root      1419 45.9 12.3 196324 94420 pts/1    Rl+  13:16 155:02 ./srcds_linux -
root      1460  0.0  0.1  11740  1128 ?        S    14:56   0:00 /usr/sbin/winbi
www-data  1510  0.0  0.4  32732  3660 ?        S    17:11   0:00 /usr/sbin/apach
root      1558  0.2  0.6  13084  4616 ?        Ss   18:53   0:00 sshd: andy [pri
andy      1635  0.0  0.2  13084  1892 ?        S    18:53   0:00 sshd: andy@pts/
andy      1636  3.1  0.4   5740  3088 pts/0    Ss   18:53   0:00 -bash
andy      1651  0.0  0.1   2712  1044 pts/0    R+   18:53   0:00 ps -aux
andy@ubuntu:~$ screen -list


```

---

### Post by renegadeandy on 2010-12-05
What i want the script to do is start a server within a screen session named csds....any ideas why this is behaving oddly?

---


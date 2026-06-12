---
title: "Memory Usage"
date: 2012-07-21
forum: General Help
---

### Post by Jorel on 2012-07-21
Hi guys,

i noticed that every time i log in to my Ubuntu file Server, my memory usage is going high... even though there's no one connected on it,,  

is there a way to minimize its usage or is it definite?

Thanks

---

### Post by sudodus on 2012-07-21
The memory usage depends on what services you have running. You can check that with top or (a nicer text interface) htop

```
sudo apt-get install htop
```

Do you use a text or graphical desktop interface? It is recommended to use only text in a server. It increases security and also saves cpu and memory for the 'real' tasks.

Anyway, when you find what programs/processes are using the most memory, you can come back here and discuss what can be switched off.

---

### Post by Jorel on 2012-07-23
Hi Sudodus,

i tried installing htop, but i got an error

E: Unable to locate package htop

is there a way-around this problem? 

thanks..

---

### Post by codemaniac on 2012-07-23
in a terminal fire the **top **command .While top is running press Shift+M to list down top resource hungry processes .

---

### Post by mmehboobhan on 2012-07-23
enter this 
# top

// it will show you.....

top - 11:56:06 up  2:46,  1 user,  load average: 0.53, 0.56, 0.59
Tasks: 163 total,   1 running, 161 sleeping,   1 stopped,   0 zombie
Cpu(s):  1.2%us,  0.5%sy,  0.0%ni, 98.3%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   3072216k total,  1717012k used,  1355204k free,   176724k buffers
Swap:  1951740k total,        0k used,  1951740k free,   926128k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 9471 sysadmin  20   0  557m  16m  10m S    2  0.5   0:00.38        gnome-terminal     
 4080 root           20   0  141m  17m 5436 S    1  0.6   2:38.05         Xorg               
 4363 sysadmin  20   0 1134m 219m  39m S    1  7.3  10:46.73     firefox            
 4312 sysadmin  20   0  663m  19m  12m S    0  0.6   0:01.98         gnome-settings-    
 5018 sysadmin  20   0  537m  51m  26m S    0  1.7   1:35.32         plugin-containe    
 9535 sysadmin  20   0  9112 1168  844 R    0  0.0   0:00.02 top

---

### Post by Jorel on 2012-07-23
Hi guys,,,

it worked,,, and here what it shows me...

top - 11:02:58 up 2:43, 1 user, load average: 0.39, 0.21, 0.16
Tasks: 96 total, 1 running, 95 sleeping, 0 stopped, 0 zombie
Cpu(s): 0.3%us, 0.0%sy, o.o%ni, 99.7%id, 1.0%wa, 0.0%hi, 0.0%si, 0.0
Mem: 1802400k total, 115408k used, 1686992k free, 13624 buffers
Swap: 1998844k total, 0k used, 1998844 free, 60696k cached

PID USER PR NI VIRT RES SHR S %CPU %MEM TIME+ COMMAND
1968 jorel 20 0 9568 5844 1496 S 0.0 0.3 0:00.62 bash
1724 root 20 0 17532 5004 4020 S 0.0 0.3 0:00.18 sshd
864 root 20 0 21380 4832 4004 S 0.0 0.3 0:00.18 smbd
983 whoopsie 20 0 24448 3780 2836 S 0.0 0.2 0:00.22 whoopsie
2066 root 20 0 13384 3572 2880 S 0.0 0.2 0:00.13 sudo
979 root 20 0 18052 2664 1988 S 0.0 0.1 0:00.20 winbindd
871 root 20 0  6664 2380 1940 S 0.0 0.1 0:00.01 sshd
1008 root 20 0 17984 2032 1336 S 0.0 0.1 0:00.08 winbindd
1967 jorel 20 0 17664 1936 948 S 0.0 0.1 0:00.52 sshd
1 root 20 0  3492 1872 1248 S 0.0 0.1 0:00.92 init
1042 root 20 0 17984 1844 1152 S 0.0 0.1 0:00.03 winbindd
932 root 20 0 13304 1840 1240 S 0.0 0.1 0:00.69 nmbd
1043 root 20 0 18052 1636 920 S 0.0 0.1 0:00.02 winbindd
887 syslog 20 0 30020 1420 1068 S 0.0 0.1 0:00.16 rsyslogd
941 root 20 0 21484 1228 400 S 0.0 0.1 0:00.00 smbd
2067 root 20 0 2812 1192 936 R 0.7 0.1 0:02.15 top

---

### Post by sudodus on 2012-07-23
I guess the repo where htop resides is not included by default in the server edition, although it is in the desktop editions. But you get the same information (although not quite as easy to read) with good old ***top*** :-)

It will be easier to read if you wrap such terminal text within CODE tags (mark it and click on the # icon at the top of the editing window).

Anyway, at the moment of your top snapshot, the memory usage was quite low. 

How did you notice that every time you log in to your Ubuntu file Server, the memory usage is going high... even though there's no one connected on it?

I suggest that you run top again, when the memory usage is very high, and check the memory usage for each process. Post the output in a reply, if you want help :-)

---

### Post by Jorel on 2012-07-23
hi,

i always read my welcome message every time i log-in,, and there i noticed that when im not restarting or shutting down my server, the mem usage is sometimes at 7% to 10%...

----------------------------------------------------------
Welcome to Ubuntu 12.04 LTS (GNU/Linux 3.2.0-23-generic-pae i686)

 * Documentation:  [https://help.ubuntu.com/](https://help.ubuntu.com/)

  System information as of Mon Jul 23 12:08:05 AST 2012

  System load:    0.02             Processes:           102
  Usage of /home: 4.2% of 4.64GB   Users logged in:     1
  [COLOR="Navy"]Memory usage:   2%[/COLOR]              IP address for eth0: 92.168.1.78
  Swap usage:     0%

  Graph this data and manage this system at [https://landscape.canonical.com/](https://landscape.canonical.com/)

0 packages can be updated.
0 updates are security updates.
--------------------------------------------------------

---

### Post by sudodus on 2012-07-23
OK!

I suggest that when it is high again, you run top at once. Maybe the memory usage will decrease rapidly (and in that case it was probably the effort of logging you in that was showing). Otherwise you might find some process, that is running once in a while using considerable amount of memory. 7-10% is not bad though in my opinion.

---

### Post by greenpeace on 2012-07-23
> **sudodus said:**
> 7-10% is not bad though in my opinion.

+1 ... that's really nothing to worry about.

For more information about how RAM is managed by linux, have a little read of this page: [http://www.linuxatemyram.com/](http://www.linuxatemyram.com/)

---

### Post by Jorel on 2012-07-23
thanks for the reply guys,,

that is a relief to know that nothing is eating my ram hehehehe...


love you guys,,, thanks..

---


---
title: "Sudo apt-get CONFUSED - Sub-process /usr/bin/dpkg returned an error code (1)"
date: 2010-01-14
forum: General Help
---

### Post by Svens on 2010-01-14
Hello everybody!
I think that my computer crashed one time, while I was in middle of installing some new software, and it seems like it have made "dpkg" confused with itself - it thinks, that I still need to install "Wine", but it is allready installed, so everything is allright. But everytime, when I am upgrading or installing any kind of software, it give me this error (just an error, everything still works and installs fine):
```
Setting up wine (1.0.1-0ubuntu8) ...
kernel.printk = 4 4 1 7
net.ipv4.conf.default.rp_filter = 1
net.ipv4.conf.all.rp_filter = 1
net.ipv4.tcp_syncookies = 1
vm.mmap_min_addr = 0
net.ipv4.tcp_timestamps = 0
net.ipv4.tcp_sack = 1
net.ipv4.tcp_no_metrics_save = 1
net.core.netdev_max_backlog = 2500
net.ipv4.tcp_window_scaling = 1
net.ipv4.tcp_wmem = 10240 87380 16777216
net.ipv4.tcp_rmem = 10240 87380 16777216
net.ipv4.tcp_mem = 16777216 16777216 16777216
net.core.rmem_max = 16777216
error: "net.core wmem_max" is an unknown key
vm.swappiness = 10
dpkg: error processing wine (--configure):
 subprocess installed post-installation script returned error exit status 255
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 wine
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

What should I do?

Thank You in advance!

---

### Post by SchizmWolf on 2010-01-14
Have you tried ```
 sudo apt-get -f install 
``` ?
If your computer crashed while it was working with dpkg, then it could have interrupted a process that related to wine, thus borking wine up.

---

### Post by Svens on 2010-01-14
Thank You for your answer!
```
sudo apt-get -f install
``` gives me > svens@hp:~$ sudo apt-get -f install
[sudo] password for svens: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 moderniz&#275;tas, 0 instal&#275;tas no jauna, 0 tiks no&#326;emtas un 0 netiks moderniz&#275;tas.
1 nepiln&#299;gi instal&#275;tas vai no&#326;emtas.
After this operation, 0B of additional disk space will be used.
Setting up wine (1.0.1-0ubuntu8) ...
kernel.printk = 4 4 1 7
net.ipv4.conf.default.rp_filter = 1
net.ipv4.conf.all.rp_filter = 1
net.ipv4.tcp_syncookies = 1
vm.mmap_min_addr = 0
net.ipv4.tcp_timestamps = 0
net.ipv4.tcp_sack = 1
net.ipv4.tcp_no_metrics_save = 1
net.core.netdev_max_backlog = 2500
net.ipv4.tcp_window_scaling = 1
net.ipv4.tcp_wmem = 10240 87380 16777216
net.ipv4.tcp_rmem = 10240 87380 16777216
net.ipv4.tcp_mem = 16777216 16777216 16777216
net.core.rmem_max = 16777216
error: "net.core wmem_max" is an unknown key
vm.swappiness = 10
dpkg: error processing wine (--configure):
 subprocess installed post-installation script returned error exit status 255
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 wine
E: Sub-process /usr/bin/dpkg returned an error code (1)
svens@hp:~$ 



So it seems like that this is not the answer for this problem.

---

### Post by drs305 on 2010-01-14
It's the wine post-installation script that is causing the error. Run the command from the previous post. If that doesn't clear the error message, open nautilus as root and rename the offending file:
```

gksu nautilus /var/lib/dpkg/info

```
Rename the wine post-installation script filename. I don't use wine but it is most likely called *wine.postinst*. Rename it to something like *wine.postinst-bad*. Then run the previous apt-get command again.

---

### Post by Svens on 2010-01-14
Thank you, gentleman! The problem is solved! Amazing responsiveness! :D

---

### Post by Keeflookeem on 2010-04-09
I believe that this problem is caused by the wine post-install script when it reads the /etc/sysctl.conf file. If you've previously set your swappiness to a non-default number, wine freaks out. Simply find the line that says "swappiness=X" (X=whatever number you set there),
comment it out (put a '#' sign at the start of the line), run the "sudo apt-get -f install" command again, and that should fix it. You should be able to uncomment the swappiness line after you're done without worries.

It fixed the problem for me! :)

Maybe anyone else wanna try? I think that we've found a bug. I'm blaming WINE at the moment.

---

### Post by ibuclaw on 2010-04-09
> **Keeflookeem said:**
> 
Maybe anyone else wanna try? I think that we've found a bug. I'm blaming WINE at the moment.

Instead of blaming WINE, ask the person who is currently maintaining the package for Debian/Ubuntu. I'm sure he'll give you a good reason for it.

---


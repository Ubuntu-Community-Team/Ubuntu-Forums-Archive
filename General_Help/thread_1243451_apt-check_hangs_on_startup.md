---
title: "apt-check hangs on startup"
date: 2009-08-18
forum: General Help
---

### Post by MadCatmkII on 2009-08-18
Hello

For some reason the process 'apt-check' hangs when I log into xubuntu, eating 100% of the cpu. It seems this is why I haven't seen any update notifications for at least a week. What do I need to do to figure out why this is happening?

---

### Post by zvacet on 2009-08-18
you can always check for updates with

```
sudo apt-ge update && sudo apt-get upgrade
```

---

### Post by MadCatmkII on 2009-08-19
I know that of course, but it doesn't help the fact that a part of my linux-installation suddenly stopped working for no apparent reason. And I have to manually kill the apt-check process before I do because it apparantly locks something in /var/lib/dpkg/ 

Does anyone have a clue what might be going on?

---

### Post by ithinkitschad on 2009-08-19
> **MadCatmkII said:**
> Hello

For some reason the process 'apt-check' hangs when I log into xubuntu, eating 100% of the cpu. It seems this is why I haven't seen any update notifications for at least a week. What do I need to do to figure out why this is happening?

What do you mean "apt-check"
When is this command being used?

---

### Post by MadCatmkII on 2009-08-19
I assume apt-check is part of the automatic check for updates that is run every time you log in to the desktop. It's possible that this is unique for xubuntu and/or xfce. I assume it is run at more or less regular intervals while a user is logged in as well, since I've both seen update-notifications pop up after I'd been sitting at the computer for a while and I've seen extra instances of the process having hung in top.

Here's a snapshot of top just for kicks:


```
top - 11:22:35 up 7 min,  2 users,  load average: 1.98, 1.29, 0.59
Tasks: 135 total,   3 running, 132 sleeping,   0 stopped,   0 zombie
Cpu(s):  1.2%us,  0.3%sy, 98.5%ni,  0.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   3054556k total,   646544k used,  2408012k free,    35492k buffers
Swap:  4217020k total,        0k used,  4217020k free,   201388k cached

  PID USER        PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 3094 *login*     39  19 58488  32m 2908 R  100  1.1   6:33.78 apt-check          
 3353 root        39  19 58208  32m 2844 R   97  1.1   2:29.21 apt-check          
 2540 root        20   0  701m  30m  10m S    2  1.0   0:09.65 Xorg               
 3228 *login*     20   0  498m  66m  25m S    1  2.2   0:06.86 firefox       
```     

As you can see, here we have two instances of apt-check 'running' (more like being stone cold dead) and I assure you I didn't manually start either of them

---

### Post by MadCatmkII on 2009-08-22
Shameful bump. Will I have to resort to re-installing?

---

### Post by benjaminzsj on 2009-09-07
Hello, I just realized recently a similar problem. After I updated through Synaptic, occasionally my hard disk would start grinding and the system became practically unusable, I found the culprit was apt-check. Hope this can be fixed soon.

---

### Post by benjaminzsj on 2009-09-07
Sorry, double post

---

### Post by MadCatmkII on 2009-10-03
> **benjaminzsj said:**
> Hello, I just realized recently a similar problem. After I updated through Synaptic, occasionally my hard disk would start grinding and the system became practically unusable, I found the culprit was apt-check. Hope this can be fixed soon.

I'm afraid I haven't found a solution to the problem. but for some reason it fixed itself for a short while. Still no real clue what happened.

---


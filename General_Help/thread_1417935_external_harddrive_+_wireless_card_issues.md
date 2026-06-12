---
title: "external harddrive + wireless card issues"
date: 2010-02-27
forum: General Help
---

### Post by hessproject on 2010-02-27
okay heres the situation. i haven't used ubuntu since 7.4, i loved it, but it was a family computer. had to put windows back for the others. now my personal computer crashes, i decide to put ubuntu (9.10) on it.

now that i'm back to ubuntu... my wireless card (netgear WG311v3) is unsupported without ndiswrapper, and i have no access to a flash drive with the exception of my external harddrive, a 250gig seagate freeagent go... which i can't get ubuntu to detect.

so clearly theres an issue, i need to get the harddrive working without access to the internet, so i can get access to the internet. 

any suggestions..?

---

### Post by ercferret18 on 2010-02-27
ethernet?

---

### Post by hessproject on 2010-02-27
the router is on a seperate floor :/

---

### Post by ercferret18 on 2010-02-27
do you have a laptop that you can take to the router?

---

### Post by hessproject on 2010-02-27
i have an old old windows laptop if that works

---

### Post by ercferret18 on 2010-02-27
what happens when you plug in your external hard drive?

---

### Post by hessproject on 2010-02-27
it works fine on the windows laptop thats where i generally use it. its ntfs formatted it has mostly music and pictures on it.

---

### Post by ercferret18 on 2010-02-27
i mean as soon as you plug it in on the ubuntu computer

---

### Post by hessproject on 2010-02-27
oh. the ubuntu computer is a desktop. but the lights on the harddrive glow, but nothing happens on the ubuntu computer.

---

### Post by ercferret18 on 2010-02-27
plug it in, then right away type:

```
sudo dmesg | tail
```

and post the output here.

---

### Post by hessproject on 2010-02-28
alright. sorry if theres spelling errors or anything i am copying this from another computer remember.

domain 1: span 0 - 1 level MC
   groups: 0-1 (_cpu_power = 2048)
 CPU0 attaching NULL sched-domain
 CPU1 attaching NULL sched-domain
 CPU0 attaching sched-domain:
  domain 0: span 0-1 level SIBLING
    groups: 0 1
 CPU1 attaching sched-domain:
  domain 0: span 0-1 level SIBLING
   groups: 1 0

---

### Post by ercferret18 on 2010-02-28
try typing this in:

```
ls /dev/sdb
```

while it is plugged in

---

### Post by hessproject on 2010-02-28
ls: cannot access /dev/sdb: No such file or directory

---

### Post by ercferret18 on 2010-02-28
one last command...

```
sudo lsusb
```

---

### Post by hessproject on 2010-02-28
BUS 005 Device 001: ID ld6b:0001 Linux Foundation 1.1 root hub
BUS 003 Device 002: ID 046d:c00e Logitech, Inc. M-BJ58/M-BJ69 Optical Wheel Mouse
BUS 003 Device 001: ID ld6b:0001 Linux Foundation 1.1 root hub
BUS 004 Device 001: ID ld6b:0001 Linux Foundation 1.1 root hub
BUS 001 Device 001: ID ld6b:0002 Linux Foundation 2.0 root hub
BUS 002 Device 001: ID ld6b:0001 Linux Foundation 1.1 root hub

---


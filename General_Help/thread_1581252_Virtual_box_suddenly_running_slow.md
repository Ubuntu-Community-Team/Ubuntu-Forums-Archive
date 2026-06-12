---
title: "Virtual box suddenly running slow"
date: 2010-09-24
forum: General Help
---

### Post by lsutiger on 2010-09-24
I have a VM setup in VirtualBox of Win XP. This VM has been setup for well over 4 years. 

All of a sudden today, the VM started running very slow. I checked the task manager in Windows, nothing eating up PCU or memory there. I then ran htop. Attached is what I saw. There are many repeat processes with different PIDs. 
Is this normal?

---

### Post by robsoles on 2010-09-25
Please show the result of the command I am using after you kindly restart that computer and re-run virtualbox.

```
rob@rob-desktop:~$ ps aux | grep irt
rob      12643  0.2  1.2 500644 50164 ?        Sl   19:17   0:01 /usr/lib/virtualbox/VirtualBox
rob      12657  0.0  0.1  83600  4336 ?        S    19:17   0:00 /usr/lib/virtualbox/VBoxXPCOMIPCD
rob      12666  0.1  0.2 269388  9392 ?        Sl   19:17   0:01 /usr/lib/virtualbox/VBoxSVC --pipe 8 --auto-shutdown
rob      12733  5.3 31.7 1825116 1276852 ?     Sl   19:26   0:07 /usr/lib/virtualbox/VirtualBox --comment WinXP1 --startvm c3b4e1a3-aa86-4508-aa8d-ce239c351eba --no-startvm-errormsgbox
rob      12771  0.0  0.0   7628   924 pts/0    S+   19:29   0:00 grep --color=auto irt
rob@rob-desktop:~$ 

```

---

### Post by lsutiger on 2010-09-25
Here you go:
```
brian@brian-linux:~$ ps aux | grep irt
brian     3559  0.0  0.1  11860  3488 ?        S    Sep24   0:00 /usr/lib/virtualbox/VBoxXPCOMIPCD
brian     3568  0.0  0.2  21992  6832 ?        Sl   Sep24   0:06 /usr/lib/virtualbox/VBoxSVC --pipe 9 --auto-shutdown
brian     3583  5.6 36.0 1482248 1209140 ?     Sl   Sep24  58:04 /usr/lib/virtualbox/VirtualBox --comment WinXP Pro --startvm 2cabf6a3-9517-4083-1a85-80b52f5bc883
brian    16226  0.0  0.0   3044   796 pts/1    S+   07:24   0:00 grep irt

```

---

### Post by robsoles on 2010-09-25
Is the problem still apparent?

---

### Post by lsutiger on 2010-09-25
Not at computer now. ssh'd in to get that info. Will be back at computer on Monday.

---

### Post by Musicologynut85 on 2010-12-29
Has this been solved? I've been having the same problem...

---

### Post by lsutiger on 2010-12-29
No...It pops it's head up from time to time. I restart the VM and that usually works. If not, I reboot the linux box....

---

### Post by robsoles on 2010-12-29
OK, so I think what I was going to ask next was: 

**What version of VirtualBox are you using?**

I am using the closed source edition from [www.virtualbox.org]("http://www.virtualbox.org") (using debian/apt instructions from [www.virtualbox.org/wiki/Linux_Downloads]("http://www.virtualbox.org/wiki/Linux_Downloads")) on an Intel i7 860 @ 2.8GHz with 4Mb of RAM, I usually have two XP VMs running and at worst they grind and pause a bit if I start them both simultaneously but otherwise they sit there and purr very nicely.

**What's "different" about what you are doing or running, in the VM or the _HOST_ system, when your VM is running so slowly?**

---


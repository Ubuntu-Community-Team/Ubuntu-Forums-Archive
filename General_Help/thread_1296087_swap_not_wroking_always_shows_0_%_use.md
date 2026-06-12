---
title: "swap not wroking always shows 0 % use"
date: 2009-10-20
forum: General Help
---

### Post by sajanko on 2009-10-20
hello i am having problem with swap since the day i started to use linux and i am a new linux user tried to solve from forum but all my attempt failed...please help me out...
i have dual OS windows vista black edition and linux....
here is result of command from terminal:
sajanko@sajanko:~$ mkswap
mkswap: error: Nowhere to set up swap on?
Usage: mkswap [-c] [-v0|-v1] [-pPAGESZ] [-L label] [-U UUID] /dev/name [blocks]
sajanko@sajanko:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          3015       1129       1885          0         35        537
-/+ buffers/cache:        556       2458
Swap:         8581          0       8581
sajanko@sajanko:~$ sudo swapoff -a
[sudo] password for sajanko: 
sajanko@sajanko:~$ sudo swapon -a
sajanko@sajanko:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          3015       1129       1885          0         35        537
-/+ buffers/cache:        556       2458
Swap:         8581          0       8581
sajanko@sajanko:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe527552a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3916    31455238+   7  HPFS/NTFS
/dev/sda2            3917       10158    50134016    7  HPFS/NTFS
/dev/sda3           10159       19457    74694217+   5  Extended
/dev/sda5           10159       17037    55255536   83  Linux
/dev/sda6           17038       18131     8787523+  82  Linux swap / Solaris
/dev/sda7           18132       19457    10649600    7  HPFS/NTFS
sajanko@sajanko:~$ 


i cant suspend and hybernet my laptop may be it will solve both of my problem so
please help me 
sajan

---

### Post by slakkie on 2009-10-20
Swap is not always needed, when it is used you will notice it.

---

### Post by P4man on 2009-10-20
I guess you got other problems too, like a suspicious absence of virusses and malware ?

Welcome to linux. No need to use swap unless you need to address more RAM than you have. And if you can run vista, then you probably have enough RAM that you may never need any swap in linux.

Anyway your swap probably is initialized already. try 

```
swapon -s
```

you'll probably see sda6 as swap space. Linux swaps to a special swap partition, not a file by default. sda6 on your machine. No need to do anything special.

---

### Post by The Cog on 2009-10-20
You seem to have around 8G of working swap, although the OS doesn't seem to be using it at the moment.

I don't think your hibernation problems are anything to do with not having enough swap space. I think you need to look elsewhere for the cause of your problems.

---

### Post by sajanko on 2009-10-22
thankyou all for your response...i got this after swap -s 
sajanko@sajanko:~$ swapon -s
Filename                Type        Size    Used    Priority
/dev/sda6                               partition    8787512    0    -1
sajanko@sajanko:~$ 
Its ok if i dont need swap...but i wish i could suspend my laptop when i close my lid and resume on its own after i open but i could not do that...some time it suspends but never resumed propery i had continious black blank screen and as usual i used magic button to restart...i dont know exactly what to do as i am new ubuntu user....could you please give me hint to check this stuff....write some command to allocate where the problem lies... i tried it from power management and other hints from forum but nothing seems to work....

Thank you

---

### Post by P4man on 2009-10-22
> **sajanko said:**
> thankyou all for your response...i got this after swap -s 
sajanko@sajanko:~$ swapon -s
Filename                Type        Size    Used    Priority
/dev/sda6                               partition    8787512    0    -1
sajanko@sajanko:~$ 
Its ok if i dont need swap...but i wish i could suspend my laptop when i close my lid and resume on its own after i open but i could not do that...some time it suspends but never resumed propery i had continious black blank screen and as usual i used magic button to restart...i dont know exactly what to do as i am new ubuntu user....could you please give me hint to check this stuff....write some command to allocate where the problem lies... i tried it from power management and other hints from forum but nothing seems to work....

Thank you

Forget swap, Its there, it works, you got -as you guessed-, another problem. Perhaps you want to make a new thread with a more appropriate title (so the "right" people read it). In that thread give some details as to which laptop you have, which version of ubuntu and perhaps which (if any) restricted drivers you installed (like nvidia video drivers). The more info the better.

Another thing that can help is attach 2 log files you find in /var/log
One is called pm-suspend.log the other pm-powersave.log

---

### Post by sajanko on 2009-10-23
Thankyou my friend i will post new thread...

---


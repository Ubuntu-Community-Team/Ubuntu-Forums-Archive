---
title: "Missing .8GB of memory in MSI 7529 motherboard"
date: 2011-03-14
forum: General Help
---

### Post by gjmata on 2011-03-14
Hi,

I'm running Ubuntu 10.04.01, 64 bit, on a PC with an MSI 7529 motherboard with 4 GB of memory installed. The command 'free -m', in a terminal window, reports only 3261 MB (3.18 GB) of memory. The command 'lshw' seems to report 4GB (see below).

How can I make Ubuntu see all the memory?

Thanks in advance,

Gustavo J. Mata


Output from 'lshw':

     *-memory
          description: System Memory
          physical id: 27
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: DIMM SDRAM Synchronous
             product: PartNum0
             vendor: Manufacturer0
             physical id: 0
             serial: SerNum0
             slot: DIMM1
             size: 2GiB
             width: 64 bits
        *-bank:1
             description: DIMM SDRAM Synchronous
             product: PartNum1
             vendor: Manufacturer1
             physical id: 1
             serial: SerNum1
             slot: DIMM2
             size: 2GiB
             width: 64 bits

---

### Post by lithopsian on 2011-03-14
Do you have a 64bit kernel?  A PAE kernel?  It sounds like you are running a standard 32 bit kernel which has difficulty addressing 4GB of RAM.

---

### Post by Spyderkid on 2011-03-14
All operating systems transfer a large(ish) amount of files to you RAM to work your system,

Like at the moment I have 4GB RAM and have 2658MB left if i run 'free -m'

---

### Post by sanderj on 2011-03-14
If you download the script from [http://www.appelboor.com/check-my-hardware.py](http://www.appelboor.com/check-my-hardware.py) , and then run it with 

```
sudo python check-my-hardwpare.py
```

you'll get all the information + advices what to do.

---

### Post by lithopsian on 2011-03-14
The "total" number if free -m should report fairly close to your total RAM, regradless of what the kernel might "load".  The kernel will grab a little of this and a shared graphics card may grab some more, but it shouldn't amount to 800MB.  On my machine, there is 15MB missing from the free -m total.

---

### Post by sanderj on 2011-03-14
To run the memory-check-script from the command line, do this:


```

cd
wget http://www.appelboor.com/check-my-hardware.py
sudo python check-my-hardware.py 

```


Example output below


```



sander@athlon64:~$ cd


sander@athlon64:~$ wget http://www.appelboor.com/check-my-hardware.py
--2011-03-14 17:33:40--  http://www.appelboor.com/check-my-hardware.py
Resolving www.appelboor.com... 46.182.18.215
Connecting to www.appelboor.com|46.182.18.215|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 7396 (7.2K) [text/plain]
Saving to: `check-my-hardware.py'

100%[===================================================================================>] 7,396       --.-K/s   in 0.06s   

2011-03-14 17:33:40 (121 KB/s) - `check-my-hardware.py' saved [7396/7396]




sander@athlon64:~$ sudo python check-my-hardware.py 
[sudo] password for sander: 
check-my-hardware.py - version: SJ 2011-03-13
OK, you're root
ANALYSIS:
Total of physical memory modules found 4096 MB in 4 memory module(s)
BIOS offers 4029 MB as usable
BIOS offers 4029 MB as 'modified' usable
Memory seen by OS 3898 MB
BIOS version 10/22/2008
CPU is PAE enabled
CPU is x86_64 64-bit enabled
OS is x86_64 64-bit

SUMMARY:
Memory difference between DIMM hardware and BIOS offering 67 MB
Memory difference between BIOS offering and memory seen by OS 131 MB
Memory difference between DIMM hardware and memory seen by OS 198 MB

ADVICE:
Sorry, no advice for you

Finally: show more detailed memory info from lshw. This can take up to 30 seconds ...
       description: System Memory
       size: 4GiB
          description: DIMM DDR2 667 MHz (1.5 ns)
          size: 1GiB
          description: DIMM DDR2 667 MHz (1.5 ns)
          size: 1GiB
          description: DIMM DDR2 667 MHz (1.5 ns)
          size: 1GiB
          description: DIMM DDR2 667 MHz (1.5 ns)
          size: 1GiB

Finished
sander@athlon64:~$ 



```

HTH

---

### Post by gjmata on 2011-03-14
I am running the 64 bit version of Ubuntu (AMD 64) which most likely has a 64 bit kernel....

---

### Post by gjmata on 2011-03-14
Thanks for pointing out the script. I have run it, the output is below. Any hints?

OK, you're root
ANALYSIS:
Total of physical memory modules found 4096 MB in 2 memory module(s)
BIOS offers 4085 MB as usable
BIOS offers 6634 MB as 'modified' usable
Memory seen by OS 3261 MB
BIOS version 07/15/2008
CPU is PAE enabled
CPU is x86_64 64-bit enabled
OS is x86_64 64-bit
Summary:
Memory difference between DIMM hardware and BIOS offering -2538 MB
Memory difference between BIOS offering and memory seen by OS 3373 MB
Memory difference between DIMM hardware and memory seen by OS 835 MB
ADVICE:
Sorry, no advice for you

---

### Post by sanderj on 2011-03-14
> **gjmata said:**
> Thanks for pointing out the script. I have run it, the output is below. Any hints?

Memory seen by OS 3261 MB
BIOS version 07/15/2008



The 3200 MB is the infamous boundary. However, the reason is not clear from the script.
I would check your BIOS settings for "memory hoisting" / "memory (hole) remapping". If you find that setting, it should be on.
And I would update the BIOS (if possible)

Question: when was the Mobo introduced?

---

### Post by gjmata on 2011-03-14
> **sanderj said:**
> The 3200 MB is the infamous boundary. However, the reason is not clear from the script.
I would check your BIOS settings for "memory hoisting" / "memory (hole) remapping". If you find that setting, it should be on.
And I would update the BIOS (if possible)

Question: when was the Mobo introduced?
OK, I'll check the BIOS.

Thanks

---


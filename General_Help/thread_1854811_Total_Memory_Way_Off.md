---
title: "Total Memory Way Off?"
date: 2011-10-05
forum: General Help
---

### Post by larrytate1 on 2011-10-05
I've got 4G RAM installed and it is reported by the BIOS.  However, "free -m" reports as follows:

             total       used       free     shared    buffers
Mem:       2965196     506960    2458236          0      66236     
-/+ buffers/cache:     201988    2763208
Swap:      1463292          0    1463292

I understand why not all 4G will show up in the total but 2965196 seems WAY low.  I'm running 11.04 Natty with the PAE kernel.

---

### Post by dcstar on 2011-10-05
> **larrytate1 said:**
> I've got 4G RAM installed and it is reported by the BIOS.  However, "free -m" reports as follows:

             total       used       free     shared    buffers
Mem:       2965196     506960    2458236          0      66236     
-/+ buffers/cache:     201988    2763208
Swap:      1463292          0    1463292

I understand why not all 4G will show up in the total but 2965196 seems WAY low.  I'm running 11.04 Natty with the PAE kernel.

There are hundreds of posts already about 32-bit systems and RAM size, do a search for them.

---

### Post by larrytate1 on 2011-10-05
> **dcstar said:**
> There are hundreds of posts already about 32-bit systems and RAM size, do a search for them.

I guess I should have mentioned that there are hundreds of posts already about 32-bit systems and RAM size and that I have already searched them.  My particular case seems to be an exception, thus my post.  The examples I found when searching indicate that I should see more memory in the total.

---

### Post by sffvba[e0rt on 2011-10-05
Hi,

How much RAM does your video card have? Because if that plus this value of 3GB gets close to 4GB that would explain it...


404

---

### Post by larrytate1 on 2011-10-05
> **not found said:**
> Hi,

How much RAM does your video card have? Because if that plus this value of 3GB gets close to 4GB that would explain it...


404

My video card has 256M of RAM.  I'm just confused on why Ubuntu is reporting 1 full Gig of memory less than I have installed.

Thx

---

### Post by lensman3 on 2011-10-05
Do a "more /proc/meminfo".

---

### Post by larrytate1 on 2011-10-06
> **lensman3 said:**
> Do a "more /proc/meminfo".

This results in:

MemTotal:        2965196 kB
MemFree:          266132 kB
Buffers:           31312 kB
Cached:          2248480 kB
.
.
.

I've checked my BIOS config for anything that might "hide" some memory but everything looks right.  BIOS reports 4 slots with 1G each, total of 4G.  256M video card.  Ubuntu 11.04 with PAE kernel. Intel Grantsdale-G motherboard.  Pentium 4 3.2GHz.  Hyperthreading enabled.  Still a mystery to me.

---

### Post by dino99 on 2011-10-06
enable PAE setting into bios
install & use generic-pae kernel into synaptic (instead of generic)

[http://blog.pault.ag/post/3107062816/why-64-bit-computing-is-really-dumb-right-now](http://blog.pault.ag/post/3107062816/why-64-bit-computing-is-really-dumb-right-now)

---

### Post by larrytate1 on 2011-10-06
> **dino99 said:**
> enable PAE setting into bios
install & use generic-pae kernel into synaptic (instead of generic)

[http://blog.pault.ag/post/3107062816/why-64-bit-computing-is-really-dumb-right-now](http://blog.pault.ag/post/3107062816/why-64-bit-computing-is-really-dumb-right-now)

I installed the PAE kernel prior to my first post because I thought it might have an effect on what I was seeing even though I only have 4G RAM.  It didn't change anything.  I just checked synaptic and this is what is installed:

linux-generic-pae (ver: 2.6.38.11.26)
linux-headers-2.6.38-11-generic-pae (ver: 2.6.38.11.50)
linux-headers-generic-pae (ver: 2.6.38.11.26)
linux-image-2.6.38-11-generic-pae (ver: 2.6.38.11.50)
linux-image-generic-pae (ver: 2.6.38.11.26)

all are latest versions.  Should I change something here?  I'm kind of doubtful PAE has any bearing on the issue at hand.

---


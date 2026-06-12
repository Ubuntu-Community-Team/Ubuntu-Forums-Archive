---
title: "Ubuntu 11.04 32-Bit on MacBook  Pro 5,5. Only identifies 2.7GB of Ram, out of 4GB."
date: 2011-07-16
forum: General Help
---

### Post by rtyb on 2011-07-16
Well, I'm not really sure as to where to post this. Apple Users, or General Help?

The matter:

I (around 1 month ago) just installed Ubuntu 11.04 on my MacBook Pro 5,5 (13 Inch - Intel Core 2 Duo 2.53GHz, 4GB RAM DDR3, Nvidia GeForce 9400M graphics processor with 256MB of DDR3 SDRAM shared with main memory, etc..), and everything has worked wonderfully, Ubuntu identified most hardware on the first boot. Installed Nvidia recommender drivers, etc...

But i keep having this HUGE problem, specially since i use VirtualBox wit WinXP a lot (SimCity 4.....:)).
Ubuntu only identifies 2.7GB ouf of my 4.00GB. That makes up for some HORRENDOUS lag.
```
yerson@Yerson-MBP-Ubuntu:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          2745       2636        109          0         18        362
-/+ buffers/cache:       2255        490
Swap:          823        223        600

```

I've read...supposedly one solution (perhaps the only solution) is to install the PAE kernel, but I'm extremely cautious when it comes to PAE, specially cuz i've already had trouble with PAE before, on previous editions (MacBook Pro not booting, corrupted home partition, etc...)
Beside dunno why, neither do in know what it mean, but:

```
yerson@Yerson-MBP-Ubuntu:~$ sudo apt-get purge
[sudo] password for yerson: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.

```

then...

```
yerson@Yerson-MBP-Ubuntu:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  linux-generic linux-headers-generic linux-image-generic nautilus
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.

```
This sincerely leaves me like, WTF?

```
yerson@Yerson-MBP-Ubuntu:~$ sudo apt-get install linux-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  linux-image-2.6.38-10-generic linux-image-generic
Suggested packages:
  fdutils linux-doc-2.6.38 linux-source-2.6.38 linux-tools
The following NEW packages will be installed:
  linux-image-2.6.38-10-generic
The following packages will be upgraded:
  linux-generic linux-image-generic
2 upgraded, 1 newly installed, 0 to remove and 2 not upgraded.
Need to get 35.8 MB of archives.
After this operation, 114 MB of additional disk space will be used.

```

OF COURSE I SAY NO, i don't know what i'm about to do there.

Any help? 

Summary: I want my 4GBs of RAM, and learn through the process :D.

---

### Post by rtyb on 2011-07-17
Anyone...?
Any...?

---

### Post by jocko on 2011-07-17
> **rtyb said:**
> Well, I'm not really sure as to where to post this. Apple Users, or General Help?Here is fine. This is a general problem for both Apples and PCs...

> **rtyb said:**
> I (around 1 month ago) just installed Ubuntu 11.04 on my MacBook Pro 5,5 (13 Inch - Intel Core 2 Duo 2.53GHz, 4GB RAM DDR3, Nvidia GeForce 9400M graphics processor with 256MB of DDR3 SDRAM shared with main memory, etc..), and everything has worked wonderfully, Ubuntu identified most hardware on the first boot. Installed Nvidia recommender drivers, etc...

But i keep having this HUGE problem, specially since i use VirtualBox wit WinXP a lot (SimCity 4.....:)).
Ubuntu only identifies 2.7GB ouf of my 4.00GB.
32 bit ubuntu normally can't address more than 3-3.5 GB ram. As a workaround you can install a pae kernel.
Since you have a 64 bit cpu I'm sure you would be better off installing a 64 bit operating system.

---

### Post by rtyb on 2011-07-17
My installation only identifies 2.7GB...Shame...

So...is the PAE Kernel safe? As i mentioned before, i have had only bad experiences with it...

And...is 64-Bit Ubuntu even Stable?

From what i've read, several programs won't work under a 64-Bit enviroment...

---

### Post by jwbrase on 2011-07-17
> **rtyb said:**
> My installation only identifies 2.7GB...Shame...

So...is the PAE Kernel safe? As i mentioned before, i have had only bad experiences with it...

And...is 64-Bit Ubuntu even Stable?

From what i've read, several programs won't work under a 64-Bit enviroment...

Yes. 64-bit is stable. There are a very few programs that are only available in 32-bit, but you can generally get them to run on 64-bit using ia32libs. (Sometimes it takes a bit of work, but I've generally not found it too troublesome).

Anyways, 32-bit is supposed to address up to 4 GiB, but often the top half gigabyte or gigabyte ends up inaccessible for whatever reason. We have a desktop with 4 gigs of RAM that only sees 3.25 gigs under 32 bit WinXP.

Most of my experience with Linux has been on a 64-bit machine with 64-bit Ubuntu on it, and I can't see any reason to use 32 bit on a machine with a 64-bit processor, especially if you have more than 3 gigs of RAM. (One thing I will say, though, is that it really helps to get a machine with Linux installed by the manufacturer. That way you skip all sorts of configuration issues).

---

### Post by rtyb on 2011-07-17
When installing pae...do i have to desactivate the propietary drivers..?

---

### Post by wildmanne39 on 2011-07-17
Hi, myself I would use 64 bit, I have been using it for about five years I have never really had a problem with it.

---

### Post by rtyb on 2011-07-17
Alright then, that's it, thanks wildmanne.

I'm changing to Ubuntu 64-Bit.

I shall open a new thread then.

---

### Post by wildmanne39 on 2011-07-17
> **rtyb said:**
> Alright then, that's it, thanks wildmanne.

I'm changing to Ubuntu 64-Bit.

I shall open a new thread then.
Hi, ok would you please go to the top of the page and mark this thread solved be clicking on thread tools. Thank you so much.

---


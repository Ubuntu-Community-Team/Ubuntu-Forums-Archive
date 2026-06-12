---
title: "Is Ubuntu 10.04 64 bit ?"
date: 2011-11-26
forum: General Help
---

### Post by kappclark on 2011-11-26
Hello:
 
I have a laptop with an Intel T2330 dual core processor. I am running Ubuntu 10.04 on the laptop
 
It is a 64 bit processor..
 
Question - does Ubuntu default to 32 Bit with a "standard" installation ?? It runs fine - just curious if this could be 'upgraded' to 64 bit
 
Thank You
 
Bill Clark

---

### Post by ottosykora on 2011-11-26
ubuntu is available in 32bt and 64bit versions, it depends whaich one did you install.

The installer will however pick a kernel able to handle more ram when 64bit hardaware is detected during the installation of 32bit version.

---

### Post by bluexrider on 2011-11-26
To "upgrade" from 32bit to 64bit requires re-installation.

Unless you have over 4Gb of memory there is no reason hot to use the 32bit version.

---

### Post by haqking on 2011-11-26
> **bluexrider said:**
> To "upgrade" from 32bit to 64bit requires re-installation.

Unless you have over 4Gb of memory there is no reason hot to use the 32bit version.

That is not strictly true.

If you have more then 4GB ram then a PAE kernel will take advantage of it if still using 32 bit.  Also you can gain some performance benefits from running a 64 bit system on less than 4GB ram.

However some people argue the performance issue.

However if you have x64 bit capable hardware, i would back up my data and do a fresh install to take full advantage of a x64 OS given the choice.

Cheers

---

### Post by sudodus on 2011-11-26
There are 32- and 64-bit versions of each Ubuntu 'date-version' 10.04 LTS ... 11.10 and flavour [KLX]ubuntu. The 32-bit version works on almost all PCs. The 64-bit version needs a 64-bit processor. It makes no major difference unless you have more than ~3-4 GB of RAM or some special software that takes advantage of the 64-bit management.

You install the versions from different iso-files. **[COLOR=SeaGreen]We have to wait for someone else to tell if it is possible to upgrade easily from 32 to 64 bit systems[/COLOR]**. Maybe if you use the configuration files according to the following post by oldfred
[http://ubuntuforums.org/showthread.php?t=1881926](http://ubuntuforums.org/showthread.php?t=1881926)

---

### Post by pbpersson on 2011-11-26
> **sudodus said:**
>  some special software that takes advantage of the 64-bit management.


Wouldn't the Linux kernel take advantage of the 64-bit hardware and therefore yield improved thread and memory management?  I would think it would run all the 32-bit software faster.

---

### Post by sudodus on 2011-11-26
Well, test a particular application in your computer to find out if it is faster or smoother ;-)

---

### Post by kappclark on 2011-11-26
Thank you all for the answers... The laptop only has 2 GB of memory (4GB max) -- it is an Acer Aspire 4720Z..
 
You have just saved me a TON of time, and I appreciate it !

---

### Post by pbpersson on 2011-11-28
> **sudodus said:**
> Well, test a particular application in your computer to find out if it is faster or smoother ;-)

I always go with 64-bit because it is more high tech.  I figure why live in the past if I have a choice.  I have never had time or been ambitious enough to install two versions on the same machine side-by-side to do a comparison.

---

### Post by sudodus on 2011-11-28
> **pbpersson said:**
> I always go with 64-bit because it is more high tech.  I figure why live in the past if I have a choice.  I have never had time or been ambitious enough to install two versions on the same machine side-by-side to do a comparison.
Well I did several years ago and recently. There used to be issues with some software packages and 64-bit technology, so I tested the speed, and found it to be approximately the same as with 32-bits. Some operations were even faster with 32 bits. At that time, obviously, I selected to run 32-bit operating systems on my 64-bit computer. The 64-bit technology is mature now, but a lot of software is probably still basically designed for 32 bits (including parts of the linux system).

---

### Post by asifnaz on 2011-11-29
I suggest you to use 32 bit unless you have some special needs

---


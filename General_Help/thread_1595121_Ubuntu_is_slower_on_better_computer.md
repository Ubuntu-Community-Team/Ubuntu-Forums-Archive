---
title: "Ubuntu is slower on better computer"
date: 2010-10-12
forum: General Help
---

### Post by philpp on 2010-10-12
Hey all,
I just installed Ubuntu 10.10 on two of my laptops. One is a Lenovo G550 and the other is a Toshiba A505. The Lenovo has an Intel Pentium Dul-Core T4500 at 2.3 GHz, 4 GB ram, and Intel Mobile 4 Graphics or something, and the Toshiba has an Intel core i7 processor at 1.6 GHz, 4 GB ram, and the NVidia GeForce 330M graphics card. Ubuntu on the Toshiba, even though it has better specs, runs considerably slower. Boot is slower, programs start and run slower, menus open slower, it's very wierd. The first time I start chrome on the Toshiba it takes like 20 seconds to come up, and each subsequent start takes about 4 seconds on the Toshiba, but is nearly instant on the Lenovo.
Why is this happening?

---

### Post by sendblink23 on 2010-10-12
> **philpp said:**
> Hey all,
I just installed Ubuntu 10.10 on two of my laptops. One is a Lenovo G550 and the other is a Toshiba A505. The Lenovo has an Intel Pentium Dul-Core T4500 at 2.3 GHz, 4 GB ram, and Intel Mobile 4 Graphics or something, and the Toshiba has an Intel core i7 processor at 1.6 GHz, 4 GB ram, and the NVidia GeForce 330M graphics card. Ubuntu on the Toshiba, even though it has better specs, runs considerably slower. Boot is slower, programs start and run slower, menus open slower, it's very wierd. The first time I start chrome on the Toshiba it takes like 20 seconds to come up.
Why is this happening?

I can tell you instantly....
Even if its an i7 - read the Processor Speed
Dual Core 2.3ghz
i7 1.6ghz

Speed is not how many cores it has... its the processing speed of the cores that matters. But i am certain 100% on the i7 even if its slower processing speed you can handle much more apps running on the same time compared to the dual core.

If its possible to overclock that i7(hoping the bios advanced settings isn't locked)...  try to push it to 2Ghz or more and you will see a vast difference

---

### Post by philpp on 2010-10-12
> **sendblink23 said:**
> I can tell you instantly....
Even if its an i7 - read the Processor Speed
Dual Core 2.3ghz
i7 1.6ghz

Speed is not how many cores it has... its the processing speed of the cores that matters. But i am certain 100% on the i7 even if its slower processing speed you can handle much more apps running on the same time compared to the dual core.

So... even though it's 8 cores at 1.6 it's slower than 2 cores at 2.3? That's wierd, so this isn't Ubuntu's fault at all.

That kinda sucks about the processor. I bought the laptop because I thought i7's were fast D:

---

### Post by JackNocturne on 2010-10-12
Also the Speed of the HDD in **RPM** affects accessibility of date(and therefore applications) considerably.

---

### Post by sendblink23 on 2010-10-12
> **philpp said:**
> So... even though it's 8 cores at 1.6 it's slower than 2 cores at 2.3? That's wierd, so this isn't Ubuntu's fault at all.

That kinda sucks about the processor. I bought the laptop because I thought i7's were fast D:

Its not really 8 cores, its actually 4 cores - the 8 cores are only available when you have Hyper Threading enabled 

> What is Hyper-Threading? It's when the processor splits itself into two virtual processors in order to share the workload 

So having only a speed of 1.6ghz on which I am not joking... that is the speed of a regular Acer One tiny laptops.. won't help much at all
Next time when buying a laptop Pay Attention to the Processing Speed *Ghz*

---

### Post by Ranko Kohime on 2010-10-12
I don't see any reason why 1.6GHz should be *slow*, regardless.  I can start Firefox faster than the OP can start Chrome, on my 900MHz single-core CELERON (Boo, hiss).

Firefox starts slower on my Mac with a dual-core 1.83GHz processor, but that's due entirely to the number of tabs I save on my desktop, which usually numbers into the dozens.  On a fresh start with no tabs we're talking no more than about 10 seconds first start after a reboot.

And comparatively, my 400MHz HP used to start up Opera faster than 20 seconds.

---

### Post by sendblink23 on 2010-10-13
I'd imagine you have rebooted a few times already..... Have you tried booting Ubuntu into safe mode on low graphics mode, to see if it still acts same slow? Also have you installed the Nvidia driver from S>A>AD ?

If its still slow... then lets do this... try again another clean install of 10.10 on the i7, maybe something did go wrong while installing the OS on that machine.

I somehow started thinking that its odd(because the hardware is actually allot better)... I called a buddy to bring me his acer one which is 1.6ghz with 1.5gb ram & 950gma, and he had installed 10.10(not the netbook remix, he used the desktop edition).. he told me the 1st time he installed it.. it was a bit jerky(as in a bit too slow) the system so then he decided to re-install it again and afterwards it reacted much faster the system.... that is why I'm suggesting it to you to try re-installing on that machine maybe it may help

If none of this helps... then i have no other ideas

---

### Post by PaulReaver on 2010-10-13
more cores only help on multi-threaded applications,  
and the nvidia won't help any with booting...

although

my little 1.6ghz netbook (with multithreading)

boots faster than my 3.2ghz pentium4 (without multithreading)

so more 'cores' definitely help with boot speed. 
:confused:

---


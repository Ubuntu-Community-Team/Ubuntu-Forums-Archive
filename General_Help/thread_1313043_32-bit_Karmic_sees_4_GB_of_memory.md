---
title: "32-bit Karmic sees 4 GB of memory?"
date: 2009-11-03
forum: General Help
---

### Post by bovender on 2009-11-03
Hello,

out of curiosity: I am running 32-bit Karmic on a Thinkpad T61 with 4 GB physical RAM. System monitor reports 3.9 GB. Windows would only see 3 GB, and I thought this was due to the 32 bit OS. How come that Karmic reports more? (The only change that I made in the BIOS since the change to Ubuntu was to enable virtualization technology.)

Thanks

lazy

---

### Post by Sef on 2009-11-03
With [PAE]("http://en.wikipedia.org/wiki/Physical_Address_Extension"), a 32-bit system can see more than 3.2 gb ram.

---

### Post by renkinjutsu on 2009-11-03
Karmic's desktop kernel comes with PAE enabled?

---

### Post by cb951303 on 2009-11-03
> **renkinjutsu said:**
> Karmic's desktop kernel comes with PAE enabled?

there is an extra package called linux-generic-pae but it's not installed by default

@OP do you have linux-generic-pae installed?

---

### Post by JBAlaska on 2009-11-03
[quote="Karmic Beta Page"]The 32-bit PAE desktop kernel (linux-image-generic-pae) now also provides the PAE mode needed for hardware with the NX CPU feature.[/quote] I think it's in karmic by default

---

### Post by 0cton on 2009-11-03
on 32 bit systems 4 GB of RAM is available, but the kernel usually reserves some witch is "invisible" to  the system.
Windows reserves usually more than linux (not even a fixed amount for  I think but a %)
I have 512 mb but it reports 503
and even integrated videocards can reserve some memory.
with PAE you could use more than 4 gb of ram but still only 4 gb would be "visible" at a time.
Also I've read as well that is going to be by default in karmic, and except servers , even thought from pentium 3 it is supported, at home people rarely have more than 4gb even on 64 bit systems

---

### Post by dcstar on 2009-11-03
> **lazy_leukocyte said:**
> Hello,

out of curiosity: I am running 32-bit Karmic on a Thinkpad T61 with 4 GB physical RAM. System monitor reports 3.9 GB.
......

System Monitor does **not** report "3.9 **GB**", it reports in **GiB**, there is a difference.

---

### Post by cb951303 on 2009-11-04
> **dcstar said:**
> System Monitor does **not** report "3.9 **GB**", it reports in **GiB**, there is a difference.

in that case he should see even more.

---

### Post by bovender on 2009-11-04
@cb951303: It must be enabled by default, system monitor says I am running kernel 2.6.31-14-generic-pae

What I find puzzling is that Windows XP Professional SP3 never reported that much memory, even though it should be able to use PAE.

Yet another reason for switching to Linux... ;-)

---

### Post by Uncle Spellbinder on 2009-11-04
For those wanting more info in Physical Address Extension (PAE), informative read at Wikipedia here:

[http://en.wikipedia.org/wiki/Physical_Address_Extension](http://en.wikipedia.org/wiki/Physical_Address_Extension)

---

### Post by cb951303 on 2009-11-04
> **lazy_leukocyte said:**
> @cb951303: It must be enabled by default, system monitor says I am running kernel 2.6.31-14-generic-pae

What I find puzzling is that Windows XP Professional SP3 never reported that much memory, even though it should be able to use PAE.

Yet another reason for switching to Linux... ;-)

that's odd. I have fresh karmic install and here is the "uname -a" result

```

Linux xxxx-desktop **2.6.31-14-generic** #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686 GNU/Linux

```

no pae for me :confused:

---

### Post by bovender on 2009-11-04
When I type uname -a I get this:

```
Linux Seppel4 2.6.31-14-generic-pae #48-Ubuntu SMP Fri Oct 16 15:22:42 UTC 2009 i686 GNU/Linux
```

---

### Post by Monotoko on 2009-11-04
and i get:

```
Linux Katie-II 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:05:01 UTC 2009 x86_64 GNU/Linux
```

---

### Post by zeroluck on 2009-11-07
me too! me too!

I get:

```
Linux romulo-laptop 2.6.31-14-generic-pae #48-Ubuntu SMP Fri Oct 16 15:22:42 UTC 2009 i686 GNU/Linux
```

---


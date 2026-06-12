---
title: "No SWAP in use !! Help!"
date: 2011-02-08
forum: General Help
---

### Post by m0nstersnatch on 2011-02-08
Hello, 

I have 4GB RAM but the system performs  poorly and I think it has something to  do with the usage of swap (swap is not beeing used)

> /etc/fstab
# / was on /dev/sda1 during installation
UUID=2ac2d1b6-6b1c-44e1-ae8f-44a5616217d1  /                ext4         relatime,errors=remount-ro  0  1  
# swap was on /dev/sda2 during installation
UUID=2b145d3d-df5f-4779-bab0-2e033dc0c604  none             swap         sw                          0  0  
/mnt/512Mb.swap                            none             swap         sw                          0  0  
/dev/scd0                                  /media/cdrom0    udf,iso9660  user,noauto,exec,utf8       0  0  
/dev/fd0                                   /media/floppy0   auto         rw,user,noauto,exec,utf8    0  0  
/dev/sda3                                  /media/MRBIG     ext4          users,user                  0  2> sudo blkid -c /dev/null
/dev/sda1: UUID="2ac2d1b6-6b1c-44e1-ae8f-44a5616217d1" TYPE="ext4" 
/dev/sda2: UUID="2b145d3d-df5f-4779-bab0-2e033dc0c604" TYPE="swap" 
/dev/sda3: LABEL="MRBIG" UUID="0586fac1-aa46-4b26-a19e-436b577521f0" TYPE="ext4"> sudo fdisk -l
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2745    22049181   83  Linux
/dev/sda2            2746        3060     2530237+  82  Linux swap / Solaris
/dev/sda3            3061       38913   287989222+  83  Linux> free -l
             total       used       free     shared    buffers     cached
Mem:       3614012    1796944    1817068          0      28668    1239988
Low:        853876     147476     706400
High:      2760136    1649468    1110668
-/+ buffers/cache:     528288    3085724
Swap:      3054508          0    3054508As you can see the swap  is not beeing used, but there is a /mnt/512Mb.swap which I cannot recall  making. What is this all about ?

Thanks !

---

### Post by aeiah on 2011-02-08
how strange. it seems your pc is reading both your 2.5gb and .5gb swaps. dont know how /mnt/512Mb.swap got there without your doing though :p when was it created? it looks likely that at one point you followed this: [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

anyway.. the reason you arent using your swap is because you've got 4GB of ram. under normal use my system never uses the swap. its using about a gig of ram right now with these running, amongst others: mpd, urxvtc, chromium (9 tabs), tsclient, thunar, evince, skype

---

### Post by yesrno on 2011-02-08
Exactly what aeiah said, with 4gig of ram it's normal the SWAP isn't used. Simply because it isn't needed. But what do you mean by "performs poorly" ?

---

### Post by vanadium on 2011-02-08
There is a swap partition in use, so it might be wise to remove the extra swap file that is there, apparently without any good reason.

Place a comment mark before the line:
```

/mnt/512Mb.swap none swap sw 0 0

```

Indeed, you will need to clarify "poor performance". It will also depend on your processor:
```

cat /proc/cpuinfo

```

---

### Post by m0nstersnatch on 2011-02-08
> $ cat /proc/cpuinfo
processor    : 0
vendor_id    : GenuineIntel
cpu family    : 15
model        : 3
model name    : Intel(R) Pentium(R) 4 CPU 3.00GHz
stepping    : 4
cpu MHz        : 2992.702
cache size    : 1024 KB
physical id    : 0
siblings    : 2
core id        : 0
cpu cores    : 1
apicid        : 0
initial apicid    : 0
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 5
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe constant_tsc pebs bts pni dtes64 monitor ds_cpl cid xtpr
bogomips    : 5985.40
clflush size    : 64
cache_alignment    : 128
address sizes    : 36 bits physical, 32 bits virtual
power management:

processor    : 1
vendor_id    : GenuineIntel
cpu family    : 15
model        : 3
model name    : Intel(R) Pentium(R) 4 CPU 3.00GHz
stepping    : 4
cpu MHz        : 2992.702
cache size    : 1024 KB
physical id    : 0
siblings    : 2
core id        : 0
cpu cores    : 1
apicid        : 1
initial apicid    : 1
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 5
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe constant_tsc pebs bts pni dtes64 monitor ds_cpl cid xtpr
bogomips    : 5985.34
clflush size    : 64
cache_alignment    : 128
address sizes    : 36 bits physical, 32 bits virtual
power management:I don`t have Compiz or other fancy eye candy installed and I cannot watch a flash video without it beeing choppy (it feels like 4fps) and amarok takes like a week to boot :mad: - I think Ubuntu is a really great OS, but if 4GB RAM and a double core 3GHz CPU is not enough to watch a youtube-video, something MUST be wrong! Maybe it isn`t the swap after all.. but what else could it be?!??

---

### Post by fragos on 2011-02-08
Why are you mounting your CD and FD in fstab? You don't need to do that and two swaps is also weird. I've an AMD X2 2.9Mhz, 2GB RAM, Nvidia video, 1080p monitor and cable Internet -- my system is very fast, including video.

---

### Post by m0nstersnatch on 2011-02-09
> **fragos said:**
> Why are you mounting your CD and FD in fstab? You don't need to do that and two swaps is also weird. I've an AMD X2 2.9Mhz, 2GB RAM, Nvidia video, 1080p monitor and cable Internet -- my system is very fast, including video.
I wish I could say the same..
I have removed the mountpoints for CD/FD - do those affect system performance? or its just not needed there?

Even though the swap is not used because of the amount of RAM available, I am still not happy with the performance of Ubuntu on my PC. Any advice where I can start troubleshooting?
Thanks!

---

### Post by P4man on 2011-02-09
flash video being choppy is most likely a videodriver issue. What videocard do you have, and are you using proprietary drivers for it?

Amarok taking long to start is something else, but might be related to a your fstab being a bit of a mess, not sure.

---

### Post by dino99 on 2011-02-09
which kernel is installed ? you might use generic-pae for best performance.

and dont be shy, clean your system (bleachbit, gtkorphan, gconf-cleaner can help :) )

---

### Post by m0nstersnatch on 2011-02-09
> **P4man said:**
> flash video being choppy is most likely a videodriver issue. What videocard do you have, and are you using proprietary drivers for it?
A Nvidia GeForce4 Ti 4600/AGP/SSE2 is in use with 96.43.17 drivers installed. 

The thing is, I would't complain for a little bit of poor performance when I start going crazy with tabs and 20+ applications running and compiz doing all the special effects, but the hardware I have should work fine at least for 1 application in use - so, if I start Chromium, Firefox or Opera I would gladly watch a short flash movie online w/o getting nauseous..

What else could it be?! I also cleaned the system using bleachbit. The kernel in use is 2.6.32-28-generic

---

### Post by dino99 on 2011-02-09
AGP card, forget 3d, compiz and so on

---

### Post by P4man on 2011-02-09
Almost certainly that videocard and the drivers it requires. Its 9 years old, Im shocked it even works with todays kernels (and compiz?).  Didnt nvidia end support for geforce 4 like half a decade ago?

Anyway, perhaps there is a fix, Im not sure, but at the very least Id make sure you disable desktop effects.

---

### Post by m0nstersnatch on 2011-02-10
> **dino99 said:**
> AGP card, forget 3d, compiz and so on
wow - that bad ! so, basically if my motherboard has only AGP I can forget performance improvements ? or is there an alternative to 9 yr old AGP cards ?
Thanks a lot !

---

### Post by P4man on 2011-02-10
AGP isnt the issue. If you can find a more modern videocard with an AGP interface, it should work fine as well. Problem is nVidia hasnt made anything on AGP since geforce 6 or 7 I think (and youd want at least a geforce 8 or 9 to get the full benefit of VPDAU etc). You can find fairly modern ATI cards for AGP but they cost an arm and a leg for the performance and features, and ATI isnt too great for linux.

Anyway, for $10 you should be able to find a geforce 6200 AGP or something on ebay. Its a crap card as well, but at least it can use the latest drivers. For now. Do check if your motherboard supports AGP 8x.

---

### Post by fragos on 2011-02-10
As a point of reference a year ago I was using an AGP mobo with AMD Sempron 1.6Mhz CPU and an FX5200 AGP 8X which ran Compiz successfully. A new FX6200 AGP can be had on-line for ~$40.

---

### Post by lykwydchykyn on 2011-02-10
> **dino99 said:**
> AGP card, forget 3d, compiz and so on

This is simply not true.  Plenty of AGP cards can handle 3D and compiz.  Not something as old as a geforce4, of course, but still...

---

### Post by P4man on 2011-02-10
> **lykwydchykyn said:**
> This is simply not true.  Plenty of AGP cards can handle 3D and compiz.  Not something as old as a geforce4, of course, but still...

I used to run compiz (well, actually Beryl) on a geforce2 MX! Of course, that was eons ago on ubuntu 6.06 and when X and nvidia drivers still supported that card properly. It also wasnt very fast but enough to have a 3d cube somewhat smooth.

---

### Post by m0nstersnatch on 2011-03-09
> **m0nstersnatch said:**
> A Nvidia GeForce4 Ti 4600/AGP/SSE2 is in use with 96.43.17 drivers installed. 

The thing is, I would't complain for a little bit of poor performance when I start going crazy with tabs and 20+ applications running and compiz doing all the special effects, but the hardware I have should work fine at least for 1 application in use - so, if I start Chromium, Firefox or Opera I would gladly watch a short flash movie online w/o getting nauseous..

What else could it be?! I also cleaned the system using bleachbit. The kernel in use is 2.6.32-28-generic

So now I bought a new video card: Nvidia GeForce GT430 with driver version 260.19.06 
There is now definitely improved performance regarding flash movies BUT this comes also to an end if I watch more then 1h lots of flash videos. After that it gets again shaky and sometimes even audio/video delay - not as ridiculous as before the new video card, but still...
Is this normal?! Do you experience as well such behavior ?! 
PS. I have a 1080 monitor (hp 2510), but I do not watch the flash videos in more then 720p.  1080p flash video is not working at all ;(

---


---
title: "how to check what kernel I use"
date: 2006-03-28
forum: General Help
---

### Post by syklitengutt on 2006-03-28
Is the kernel the numbers showing on my grubmenu list?
I have some difficulties running cs under wine and someone suggested 
that I should do a kernel update because of some issues with newest wine
and old kernels.
So initrd.img-2.6.12-10-386 is what the boot sais.
Will I also benifit uppgrading to 686 or k7?

---

### Post by Darkriser on 2006-03-28
yes, that's the kernel name. you can also use uname -r command.
anyway, look here for 686 kernel benefits: [http://ubuntuforums.org/showthread.php?t=143878](http://ubuntuforums.org/showthread.php?t=143878)

---

### Post by wjp.reg on 2006-03-28
uname -a

---

### Post by Darkriser on 2006-03-28
[QUOTE=wjp.reg]uname -a[/QUOTE]

that's what i meant...:oops:

---

### Post by syklitengutt on 2006-03-28
what about k7?

---

### Post by Lord Illidan on 2006-03-28
k7 is for AMD processors, like Athlon. Which processor do you have?

cat /proc/cpuinfo

---

### Post by syklitengutt on 2006-03-28
chris@chris:~$ cat /proc/cpuinfo
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 6
model           : 10
model name      : AMD Athlon(tm) XP 2800+
stepping        : 0
cpu MHz         : 2075.965
cache size      : 512 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mmxext 3dnowext 3dnow
bogomips        : 4112.38

---

### Post by syklitengutt on 2006-03-28
so I should use k7?

---

### Post by dickohead on 2006-03-28
Sure, why not? I use a K7 on my Athlon 2500 (Oc'd to 3200), it sped things up a little, but the benefits are mostly knowing how to do it, rather than a massive performance boost. But give it a try, you can always use the older one instaed if things go odd.

---

### Post by syklitengutt on 2006-03-28
just do a:
sudo apt-get install linux-k7

---


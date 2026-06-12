---
title: "Kernel-image"
date: 2006-03-28
forum: General Help
---

### Post by arjanhs on 2006-03-28
I'm using the following processor, which kernel-image is the best one to use?

processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 6
model           : 4
model name      : AMD Athlon(tm) Processor
stepping        : 2
cpu MHz         : 1096.110
cache size      : 256 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr syscall mmxext 3dnowext 3dnow
bogomips        : 2162.68

---

### Post by Sutekh on 2006-03-28
You could install 
```
sudo apt-get install linux-k7
```
This will install the latest K7 kernel image.

From what I hear there is little performance to be gained from upgrading the 386 kernel to the K7 one.  

However there may be other options that the defualt 386 kernel doesn't have that the K7 does, that may better suit your processor.  You should also try searching the forum, for more information, this is not an uncommon question.

---

### Post by dcstar on 2006-03-28
[QUOTE=Sutekh]You could install 
```
sudo apt-get install linux-k7
```
This will install the latest K7 kernel image.

From what I hear there is little performance to be gained from upgrading the 386 kernel to the K7 one.  
.......[/QUOTE]
There are many posts that I have seen claiming significant performance gains from moving off the 386 kernel to either a 686 or K7 version.

The 386 kernel is just that, something compiled for a now ancient processor command set, and not taking advantage of any of the far more advanced capabilities of more modern CPUs.

---

### Post by Sutekh on 2006-03-28
[QUOTE=dcstar]There are many posts that I have seen claiming significant performance gains from moving off the 386 kernel to either a 686 or K7 version.

The 386 kernel is just that, something compiled for a now ancient processor command set, and not taking advantage of any of the far more advanced capabilities of more modern CPUs.[/QUOTE]
I'm obviously listening to the wrong people!  I install the K7-SMP kernel for my AMD64 dual-core processor to get both cores working, I didn't think there would be a great improvement for single core CPUs though.

---


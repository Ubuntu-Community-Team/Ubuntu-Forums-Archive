---
title: "Linux K7-smp?"
date: 2006-06-02
forum: General Help
---

### Post by turbojugend_gr on 2006-06-02
Well shortly, 
I have installed the Linux-K7-SMP kernel (for multicore AMD cpus -> matching my athlon X2 4400 <- in 32bit enviroment though).

The thing is that in the boot menu it says ```
title		Ubuntu, kernel 2.6.15-23-k7
```
and it is loading:```
kernel		/boot/vmlinuz-2.6.15-23-k7 root=/dev/sda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-k7
```

I remember that when i used k8-SMP, "SMP" was refered in GRUB and loaded a kernel that ended with vmlinuz........k8-SMP.

In my System Monitor i see use information for 2 CPUs, but I am curious why is that, and also is there any longshot that only one Core is working???

Thanks in advance!

---

### Post by Sutekh on 2006-06-02
In Dapper all k7 kernels have SMP (Symmetric Multi Processing) enabled.  The linux-k7-smp package depends on the k7 kernel image.

So all is well.


If you wanna see them both working use this command to list your CPU info
```
cat /proc/cpuinfo
```
You should see both cores.

---

### Post by turbojugend_gr on 2006-06-02
thanks al ot for the info, I see them both working in system monitor s I said above. Thanks again



THREAD CLOSED

---


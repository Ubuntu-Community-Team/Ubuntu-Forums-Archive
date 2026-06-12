---
title: "im-sensors detect only coretemp"
date: 2010-01-14
forum: General Help
---

### Post by alz3abi on 2010-01-14
Hello Every body. 

i moved on ubuntu 9.10 Karmic, before on 9.04  All sensors work fine but now only "coretemp".:(
so  ran "sudo sensors-detect" and output result is:
```
#----cut here----
# Chip drivers
coretemp
#----cut here----

```sensors output:

```
root@hz:~# sensors
coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +45.0°C  (high = +100.0°C, crit = +100.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +48.0°C  (high = +100.0°C, crit = +100.0°C)  

```Loaded Kernel.

```
root@hz:~# uname -r
2.6.31-17-generic

```my laptop is Toshiba A200-1MY.
```

Intel® Centrino® Duo processor technology featuring [Intel® Core&#8482;2 Duo processor]("http://syndication.intel.com/DistributeModule.aspx?ppc_cid=IIP_02105066901&cc=CI") T7250, 
Intel® PRO/Wireless 3945ABG network connection and Intel® GM965 Express chipset                               
clock speed : 2.0 GHz                             
Front Side Bus : 800 MHz                             
2nd level cache : 2 MB
Loaded Ram: 4.0 GB (usable is 2.99 GB)
```
look forward to find an solution 
best regards
alz3abi;)

---

### Post by alz3abi on 2010-01-14
Dump

---

### Post by alz3abi on 2010-01-14
Please !!

---


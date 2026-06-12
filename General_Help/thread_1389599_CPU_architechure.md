---
title: "CPU architechure"
date: 2010-01-24
forum: General Help
---

### Post by conradin on 2010-01-24
Hi all,
I want to figure out if I have an i686 architecture device, how can I find out? I have an Intel core 2 duo.

---

### Post by llawwehttam on 2010-01-24
Easy you have x86-64

 You will be able to run 32 bit but 64 bit will be faster for you.

                                                          [IMG]http://www.intel.com/sites/sitewide/pix/badges/core/2d_62.gif[/IMG]                            **All Intel® Core&#8482;2 Duo processors feature:**

               
[LIST]
[*][Intel® dual-core technology]("http://www.intel.com/multi-core/index.htm")
[*]Enhanced Intel SpeedStep® technology
[*][Execute Disable Bit]("http://www.intel.com/technology/xdbit/index.htm")&#9674;
[*][Intel® 64 architecture]("http://www.intel.com/technology/architecture-silicon/intel64/index.htm")&#9674;
[/LIST]
             
           
                                            [http://www.intel.com/products/processor/core2duo/specifications.htm?iid=prod_core2duo+tab_spec](http://www.intel.com/products/processor/core2duo/specifications.htm?iid=prod_core2duo+tab_spec)

---

### Post by marin123 on 2010-01-24
open terminal and type in: lscpu
this provides info about cpu...

---

### Post by ibuclaw on 2010-01-24
```
grep "flags" /proc/cpuinfo
```

If you see "**lm**", your CPU is 64bit aware, if not, 32bit.

If you are curious what any of the other CPU Flags mean, see here for a brief decription: [http://ubuntuforums.org/showpost.php?p=7737401&postcount=11](http://ubuntuforums.org/showpost.php?p=7737401&postcount=11)

Regards
Iain

---

### Post by bakegoodz on 2010-01-24
A Core 2 processor can run any software made for a i686. You would have to have a desktop computer system from the mid 90's or earlier to have a compatibility problem with software made for 686. The first Pentium, K5, or even embedded AMD SC1100 processors would not be compatible.

---

### Post by conradin on 2010-01-24
Thanks For all the good ideas! lscpu told me exactly what I wanted to know!

---


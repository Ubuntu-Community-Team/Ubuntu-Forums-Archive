---
title: "Missing &quot;irq_vectors.h&quot; and Atmelwlandriver"
date: 2005-02-10
forum: General Help
---

### Post by credo on 2005-02-10
Im trying to install the Atmelwlandriver on my Warty box. I have Linux 2.6.7 installed with a full source tree, as well as Linux-Headers 2.6.8.1-3.

When I compile the atmelwlandriver, I get this:

```
In file included from /lib/modules/2.6.7/build/include/linux/irq.h:20,
                 from /lib/modules/2.6.7/build/include/asm/hardirq.h:6,
                 from 
/lib/modules/2.6.7/build/include/linux/interrupt.h:11,
                 from 
/lib/modules/2.6.7/build/include/linux/netdevice.h:515,
                 from 
/home/matt/stuff/atmelwlandriver/src/includes/pcmcia/vnet_linux.h:64,
                 from 
/home/matt/stuff/atmelwlandriver/src/includes/pcmcia/vnet.h:28,
                 from card.c:23:
/lib/modules/2.6.7/build/include/asm/irq.h:16:25: irq_vectors.h: No such 
file or directory
In file included from /lib/modules/2.6.7/build/include/asm/hardirq.h:6,
                 from 
/lib/modules/2.6.7/build/include/linux/interrupt.h:11,
                 from 
/lib/modules/2.6.7/build/include/linux/netdevice.h:515,
                 from 
/home/matt/stuff/atmelwlandriver/src/includes/pcmcia/vnet_linux.h:64,
                 from 
/home/matt/stuff/atmelwlandriver/src/includes/pcmcia/vnet.h:28,
                 from card.c:23:
/lib/modules/2.6.7/build/include/linux/irq.h:70: error: `NR_IRQS' 
undeclared here (not in a function)
In file included from /lib/modules/2.6.7/build/include/linux/irq.h:72,
                 from /lib/modules/2.6.7/build/include/asm/hardirq.h:6,
                 from 
/lib/modules/2.6.7/build/include/linux/interrupt.h:11,
                 from 
/lib/modules/2.6.7/build/include/linux/netdevice.h:515,
                 from 
/home/matt/stuff/atmelwlandriver/src/includes/pcmcia/vnet_linux.h:64,
                 from 
/home/matt/stuff/atmelwlandriver/src/includes/pcmcia/vnet.h:28,
                 from card.c:23:
/lib/modules/2.6.7/build/include/asm/hw_irq.h:28: error: 
`NR_IRQ_VECTORS' undeclared here (not in a function)
/lib/modules/2.6.7/build/include/asm/hw_irq.h:32: error: `NR_IRQS' 
undeclared here (not in a function)
make[3]: *** [card.o] Error 1
make[3]: Leaving directory 
`/home/matt/stuff/atmelwlandriver/src/Pcmcia_Pci'
make[2]: *** [revd] Error 2
make[2]: Leaving directory 
`/home/matt/stuff/atmelwlandriver/src/Pcmcia_Pci'
make[1]: *** [all] Error 1
make[1]: Leaving directory 
`/home/matt/stuff/atmelwlandriver/src/Pcmcia_Pci'
make: *** [all] Error 1
```

Then, when I try and find "irq_vectors.h", I get this:

```
root@MattLaptop:/home/matt/stuff/atmelwlandriver # find / -iname 
irq_vectors.h -follow 
find: /dev/fd/4: No such file or directory
find: /etc/printcap: No such file or directory
/lib/modules/2.6.7/build/include/asm/mach-voyager/irq_vectors.h
/lib/modules/2.6.7/build/include/asm/mach-default/irq_vectors.h
find: /lib/modules/2.6.7/build/include/asm/irq_vectors.h: No such file 
or directory
/lib/modules/2.6.7/build/include/asm/mach-pc9800/irq_vectors.h
/lib/modules/2.6.7/build/include/asm/mach-visws/irq_vectors.h
/lib/modules/2.6.7/build/include/asm-um/irq_vectors.h
/lib/modules/2.6.7/build/include/asm-i386/mach-voyager/irq_vectors.h
/lib/modules/2.6.7/build/include/asm-i386/mach-default/irq_vectors.h
find: /lib/modules/2.6.7/build/include/asm-i386/irq_vectors.h: No such 
file or directory
/lib/modules/2.6.7/build/include/asm-i386/mach-pc9800/irq_vectors.h
/lib/modules/2.6.7/build/include/asm-i386/mach-visws/irq_vectors.h
find: /lib/modules/2.6.8.1/build: No such file or directory
find: /lib/modules/2.6.8.1/source: No such file or directory
find: /usr/lib/ispell/default.hash: No such file or directory
find: /usr/lib/ispell/default.aff: No such file or directory
/usr/src/kernel-source-2.6.7/include/asm/mach-voyager/irq_vectors.h
/usr/src/kernel-source-2.6.7/include/asm/mach-default/irq_vectors.h
find: /usr/src/kernel-source-2.6.7/include/asm/irq_vectors.h: No such 
file or directory
/usr/src/kernel-source-2.6.7/include/asm/mach-pc9800/irq_vectors.h
/usr/src/kernel-source-2.6.7/include/asm/mach-visws/irq_vectors.h
/usr/src/kernel-source-2.6.7/include/asm-um/irq_vectors.h
/usr/src/kernel-source-2.6.7/include/asm-i386/mach-voyager/irq_vectors.h
/usr/src/kernel-source-2.6.7/include/asm-i386/mach-default/irq_vectors.h
find: /usr/src/kernel-source-2.6.7/include/asm-i386/irq_vectors.h: No 
such file or directory
/usr/src/kernel-source-2.6.7/include/asm-i386/mach-pc9800/irq_vectors.h
/usr/src/kernel-source-2.6.7/include/asm-i386/mach-visws/irq_vectors.h
/usr/src/linux/include/asm/mach-voyager/irq_vectors.h
/usr/src/linux/include/asm/mach-default/irq_vectors.h
find: /usr/src/linux/include/asm/irq_vectors.h: No such file or 
directory
/usr/src/linux/include/asm/mach-pc9800/irq_vectors.h
/usr/src/linux/include/asm/mach-visws/irq_vectors.h
/usr/src/linux/include/asm-um/irq_vectors.h
/usr/src/linux/include/asm-i386/mach-voyager/irq_vectors.h
/usr/src/linux/include/asm-i386/mach-default/irq_vectors.h
find: /usr/src/linux/include/asm-i386/irq_vectors.h: No such file or 
directory
/usr/src/linux/include/asm-i386/mach-pc9800/irq_vectors.h
/usr/src/linux/include/asm-i386/mach-visws/irq_vectors.h
/usr/src/linux-headers-2.6.8.1-3/include/asm/mach-voyager/irq_vectors.h
/usr/src/linux-headers-2.6.8.1-3/include/asm/mach-default/irq_vectors.h
find: /usr/src/linux-headers-2.6.8.1-3/include/asm/irq_vectors.h: No 
such file or directory
/usr/src/linux-headers-2.6.8.1-3/include/asm/mach-visws/irq_vectors.h
/usr/src/linux-headers-2.6.8.1-3/include/asm-i386/mach-voyager/irq_vectors.h
/usr/src/linux-headers-2.6.8.1-3/include/asm-i386/mach-default/irq_vectors.h
find: /usr/src/linux-headers-2.6.8.1-3/include/asm-i386/irq_vectors.h: 
No such file or directory
/usr/src/linux-headers-2.6.8.1-3/include/asm-i386/mach-visws/irq_vectors.h
find: /usr/share/doc/g++/cpp: Too many levels of symbolic links
find: /usr/share/doc/cpp/cpp: Too many levels of symbolic links
find: /usr/share/doc/gcc/cpp: Too many levels of symbolic links
find: /usr/share/dict/words: No such file or directory
find: /usr/share/texmf/dvips/base/psfonts.map: No such file or directory
/usr/include/asm/mach-voyager/irq_vectors.h
/usr/include/asm/mach-default/irq_vectors.h
/usr/include/asm/mach-pc9800/irq_vectors.h
/usr/include/asm/mach-visws/irq_vectors.h
find: /.dev/fd/4: No such file or directory
find: /.dev/dsp: No such file or directory
find: /.dev/adsp: No such file or directory
find: /.dev/midi: No such file or directory
find: /.dev/amidi: No such file or directory
find: /.dev/audio: No such file or directory
find: /.dev/mixer: No such file or directory
find: /.dev/sequencer2: No such file or directory
find: /proc/self/task/4582/fd/4: No such file or directory
find: /proc/self/fd/4: No such file or directory
find: /proc/2/task/2/exe: No such file or directory
find: /proc/2/exe: No such file or directory
find: /proc/3/task/3/exe: No such file or directory
find: /proc/3/exe: No such file or directory
find: /proc/4/task/4/exe: No such file or directory
find: /proc/4/exe: No such file or directory
find: /proc/5/task/5/exe: No such file or directory
find: /proc/5/exe: No such file or directory
find: /proc/22/task/22/exe: No such file or directory
find: /proc/22/exe: No such file or directory
find: /proc/23/task/23/exe: No such file or directory
find: /proc/23/exe: No such file or directory
find: /proc/35/task/35/exe: No such file or directory
find: /proc/35/exe: No such file or directory
find: /proc/36/task/36/exe: No such file or directory
find: /proc/36/exe: No such file or directory
find: /proc/38/task/38/exe: No such file or directory
find: /proc/38/exe: No such file or directory
find: /proc/37/task/37/exe: No such file or directory
find: /proc/37/exe: No such file or directory
find: /proc/278/task/278/exe: No such file or directory
find: /proc/278/exe: No such file or directory
find: /proc/279/task/279/exe: No such file or directory
find: /proc/279/exe: No such file or directory
find: /proc/292/task/292/exe: No such file or directory
find: /proc/292/exe: No such file or directory
find: /proc/312/task/312/exe: No such file or directory
find: /proc/312/exe: No such file or directory
find: /proc/1948/task/1948/exe: No such file or directory
find: /proc/1948/exe: No such file or directory
find: /proc/1963/task/1963/exe: No such file or directory
find: /proc/1963/exe: No such file or directory
find: /proc/2631/task/2631/fd/14/printcap: No such file or directory
find: /proc/2631/fd/14/printcap: No such file or directory
find: /proc/2651/task/2651/fd/7/printcap: No such file or directory
find: /proc/2651/fd/7/printcap: No such file or directory
find: /proc/3022/task/3022/cwd/fd/4: No such file or directory
find: /proc/3022/cwd/fd/4: No such file or directory
find: /proc/3023/task/3023/cwd/fd/4: No such file or directory
find: /proc/3023/cwd/fd/4: No such file or directory
find: /proc/3024/task/3024/cwd/fd/4: No such file or directory
find: /proc/3024/cwd/fd/4: No such file or directory
find: /proc/3025/task/3025/cwd/fd/4: No such file or directory
find: /proc/3025/cwd/fd/4: No such file or directory
find: /proc/3026/task/3026/cwd/fd/4: No such file or directory
find: /proc/3026/cwd/fd/4: No such file or directory
find: /proc/3027/task/3027/cwd/fd/4: No such file or directory
find: /proc/3027/cwd/fd/4: No such file or directory
find: /proc/4456/task/4456/exe: No such file or directory
find: /proc/4456/exe: No such file or directory
find: /proc/4457/task/4457/exe: No such file or directory
find: /proc/4457/exe: No such file or directory
find: /proc/4582/task/4582/fd/4: No such file or directory
find: /proc/4582/fd/4: No such file or directory
find: /vmlinuz: No such file or directory
```

It seems as though I have no "irq_vectors.h" file for asm-386, mach-generic - all I have is a bunch of symlinks all pointing to nowhere.

Any ideas?

---


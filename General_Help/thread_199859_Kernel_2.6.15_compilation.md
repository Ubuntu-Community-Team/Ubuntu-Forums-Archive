---
title: "Kernel 2.6.15 compilation"
date: 2006-06-19
forum: General Help
---

### Post by viraptor on 2006-06-19
I've downloaded latest linux-source package, but I'm unable to compile it. Apart from some usb wireless driver (didn't compile, so was turned off - don't remeber which one - I wanted a stripped version anyway) I got stuck with:
```
  LD      .tmp_vmlinux1
drivers/built-in.o:(.bss+0x5cc0): multiple definition of `debug'
arch/i386/kernel/built-in.o: first defined here
```
I've started with original /boot/config.... I thought that one was supposed to compile with no problems? I'm running that one after all.
What should I do to compile this config?

---

### Post by flargen on 2006-06-19
Just wondering, is there any reason why you are compiling a kernel? I think the stock ubuntu kernel already has almost everything enabled.

---

### Post by viraptor on 2006-06-19
[QUOTE=flargen]...stock ubuntu kernel already has almost everything enabled.[/QUOTE]
Oh my! You've found the reason yourself :D

```
viraptor@hedgehog:~$ lsmod | grep -v "^Module" | wc -l
88
```
Don't like

Loaded:
- parport - I haven't got parallel p.
- joydev - in laptop? :)
- sony_acpi, pcc_acpi - no vaio, no ppc - joking?
- bluetooth - no bt here either
- cpufreq_* - sorry - previous generation proc - no frequency change
and the list goes on and on ;)

---

### Post by flargen on 2006-06-19
But if certain hardware is not present its drivers are not loaded (and if they are loaded they don't do anything), so there should be no difference. But, as it's on topic, you could simply disable the unused services such as bluetooth and cpufreq, which should prevent the attempted loading of these drivers. There are tutorials and information for this on the forums and elsewhere.

So my advice is - disable as many useless services as you can. (But be careful not to disable anything important! ;) )

If you insist on compiling a kernel, maybe you should go for a newer version and apply some patches (-ck or -beyond, beyond is my favourite!). This should give you increased performance and you can remove everything that you want. You can even make a ubuntu .deb of the kernel for ease of installation!
Hope I helped you!

---

### Post by viraptor on 2006-06-19
Nope - I still want to create a stripped down version of currently used kernel to try, whether it solves my (not only) [dvd recording issue]("http://ubuntuforums.org/showthread.php?t=182415").

Back to topic - any ideas, why it doesn't compile with original, or stripped-down original config?

---

### Post by rklauco on 2006-06-30
Hi.
Did you solve it somehow?
I am trying to compile a kernel on my own with very limited amount of services/drivers etc. and I end up with the same message when making LD .tmp_vmlinuz.
Basicaly just the number after .bss differs.

I am using gcc4 and I have no idea how to continue.
Any ideas/advices?

---

### Post by patrickfromspain on 2006-06-30
In fact, disabling what you don't need does make a difference. In my case, I've reduced my boot time in nearly 40 seconds... not bad eh?

I also had that problem.. I ended up doing small changes, compile a kernel. Another set of small changes and compile, and so on... In the end, I ended with 16 kernels compiled, and the last works like a charm :D

---

### Post by rklauco on 2006-06-30
[QUOTE=patrickfromspain]I ended up doing small changes, compile a kernel. Another set of small changes and compile, and so on... In the end, I ended with 16 kernels compiled, and the last works like a charm :D[/QUOTE]
Does not sound bad - in fact I am unable to compile kernel source downloaded directly from ubuntu :-)
By disabling few USB net devices I was able to compile it.
Anyhow, I am compiling on PII 366MHz with 192MB RAM. And compile 16 kernel versions on this one could take few weeks :-)
I spent 3 days on removing various modules and continue compiling...

And one more question.
Is there some way how to compile and store the output in other folder than the source one? e.g. the output will be in /usr/src/kernel-v001, v002, ...

---

### Post by viraptor on 2006-06-30
[QUOTE=rklauco]Did you solve it somehow?[/QUOTE]
After MANY recompiles, nothing changed - I still can't find which object files export the 'debug' symbol that collides when linking. Anyone knows how to list exported symbols from .o file?

---


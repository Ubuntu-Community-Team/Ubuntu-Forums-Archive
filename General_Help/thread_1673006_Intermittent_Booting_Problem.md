---
title: "Intermittent Booting Problem"
date: 2011-01-21
forum: General Help
---

### Post by matt.garriott on 2011-01-21
Hello Everyone,

When booting my laptop will intermittently boot INCREDIBLY slow. By this I mean that it will sit on the processor flash screen for several minutes before moving on to the blinking cursor prior to the loading of the boot-loader.

This happens around 1 out of every 5 boots. I usually just do a hard shut-down (not good I know, but I'm not sure what else to do the get it working), and when I turn it back on, it generally boots normally. This has only started happening after I installed Ubuntu 10.10 about 3 or 4 weeks ago.

I have had previous versions of Ubuntu on this laptop without any negative side effects, and there doesn't appear to be any errors other than this during startup. I am guessing that it has something to do with the boot-loader because the problem is occuring before the operating system even attempts to load, but the fact that it is intermittent makes it a very confusing problem.

Here are my laptop's Specs:


Manufacturer: Toshiba

Model: Satellite A215

Processor: AMD Turion 64 X2 Mobile Technology TL-64 2.20GHz

Memory: 3070 MB

System Type: 32-bit OS

I dual boot between windows vista, and Ubuntu 10.10, I have the default Grub boot loader that comes with the Ubuntu install.

Thanks in advance for any help provided.

-Matt

---

### Post by Minn3h on 2011-01-21
If it's sitting on the BIOS screen for several minutes before it gets to the bootloader then it's not likely a problem with the bootloader or either OS. I would look for patterns in what peripherals are plugged in when the boot is slow. Maybe try updating the BIOS... Usually hangs that early are hardware-related. Unless I misunderstand and the hang is happening when the bootloader is loading.

---

### Post by matt.garriott on 2011-01-21
No it hangs prior to the boot loader. I just don't know why this problem would crop up only after I had installed Ubuntu. Else I would be sure it was a hardware problem as well.

Thanks for the suggestion, I will be sure to check for any additional peripherals that are plugged in during the boot.

-Matt

---


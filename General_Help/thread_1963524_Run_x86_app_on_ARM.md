---
title: "Run x86 app on ARM"
date: 2012-04-22
forum: General Help
---

### Post by PaceyIV on 2012-04-22
I've got a CLI app for Windows and for GNU\Linux, both compiled for x86 architecture.
Is there a way to run this app on an armel processor? Is there some emulation project for doing this thing?

Thanks for your help
Albano

---

### Post by thenixedreport on 2012-04-22
You may want to look into using Qemu as emulation would be your only option when talking about a different architecture.

---

### Post by PaceyIV on 2012-04-22
I've got less then 512 MB for RAM. Is it enough?

---

### Post by sanderj on 2012-04-22
> **PaceyIV said:**
> I've got less then 512 MB for RAM. Is it enough?

How much RAM does the CLI app use on native Windows or Linux?

---

### Post by PaceyIV on 2012-04-22
Not much!

I'm trying to run qemu but often I've got this error message:
```

$ qemu -hda idrive.img -cdrom mini.iso -boot d -m 96 -localtime -nographic -redir tcp:2232::22
qemu: malloc.c:3097: sYSMALLOc: Assertion `(old_top == (((mbinptr) (((char *) &(
(av)->bins[((1) - 1) * 2])) - __builtin_offsetof (struct malloc_chunk, fd)))) &&
 old_size == 0) || ((unsigned long) (old_size) >= (unsigned long)((((__builtin_o
ffsetof (struct malloc_chunk, fd_nextsize))+((2 * (sizeof(size_t))) - 1)) & ~((2
 * (sizeof(size_t))) - 1))) && ((old_top)->size & 0x1) && ((unsigned long)old_en
d & pagemask) == 0)' failed.
Abortito

```

I also some problem using qemu on ssh. I use my server only with ssh and I can get the qemu output.

---

### Post by PaceyIV on 2012-04-22
Now I can boot qemu but I can't pass this point

```

[    1.264096] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[    1.408369] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    1.428088] ..MP-BIOS bug: 8254 timer not connected to IO-APIC
[    1.428088] ...trying to set up timer (IRQ0) through the 8259A ..
[    1.428088] ..... (found apic 0 pin 2) ...
[    1.448117] ....... failed.
[    1.448126] ...trying to set up timer as Virtual Wire IRQ...
[   29.425865] BUG: soft lockup - CPU#0 stuck for 22s! [swapper:1]

```

I've kernel panic: fail to sync and more..

I boot my qemu with this command
```

$ qemu-system-i386 -k it -rtc base=localtime,clock=host -hda idrive.img -cdrom mini.iso -boot d -m 96 -nographic -kernel vmlinuz -append "root=/dev/sda1 console=ttyS0 acpi=off" -initrd initrd.gz -no-acpi -no-hpet -no-reboot

```

I use the debian kernel testing.

---


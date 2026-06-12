---
title: "Cant input in QEMU on Backtrack 5 (Based on Ubuntu)"
date: 2011-06-30
forum: General Help
---

### Post by lionaneesh on 2011-06-30
Hey Guyz! 

After searching for solution on GOOGLE for more than 2 hours i finally give up and need some Help 

I am trying to solve a [Shell-Storm Challenge]("http://www.shell-storm.org/wargame/b70cbd23c7c4cc161eba4ea160a8e881.php")

It consists of reversing a SH4 ELF.

```

root@bt:~# file DecodedBase64.bin 
DecodedBase64.bin: ELF 32-bit LSB executable, Renesas SH, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.26, not stripped

```I have installed [COLOR=Red]QEMU [/COLOR]and Have downloaded a  [Debian Sid sh4 image for QEMU]("http://people.debian.org/%7Eaurel32/qemu/sh4/")

As the instruction said i downloaded those images , and ran :-

```

qemu-system-sh4 -M r2d -kernel vmlinuz-2.6.32-5-sh7751r -initrd initrd.img-2.6.32-5-sh7751r -hda debian_sid_sh4_standard.qcow2 -append "root=/dev/sda1 console=tty0 noiotrap" 
```
[COLOR=Red]The Problem :-[/COLOR]

It works fine and successfully boots the machine , But i am unable to input anything when it asks for username and password!

---


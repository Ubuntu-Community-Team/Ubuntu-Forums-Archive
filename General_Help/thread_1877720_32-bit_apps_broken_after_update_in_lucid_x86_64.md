---
title: "32-bit apps broken after update in lucid x86_64"
date: 2011-11-08
forum: General Help
---

### Post by driesz on 2011-11-08
Hello.

This morning I ran "apt-get update" and "apt-get upgrade" on my 10.04 x86_64 workstation and after rebooting found that all 32-bit binaries now fail with "Segmentation fault."

As a test, I compiled a simple "int main() {}" C program using "gcc -m32" and got the same thing.  When I run it in gdb, the first thing it says is:

```
warning: the debug information found in "/lib/ld-2.11.1.so"  does not match "/lib/ld-linux.so.2" (CRC mismatch).

```And the stack trace looks like:

```
#0  0xf7fdf425 in __kernel_vsyscall ()
#1  0xf7efd3e4 in _exit () from /lib32/libc.so.6
#2  0xf7e93448 in ?? () from /lib32/libc.so.6
#3  0xf7e934ff in exit () from /lib32/libc.so.6
#4  0xf7e7abde in __libc_start_main () from /lib32/libc.so.6
#5  0x08048321 in _start ()

```I have another machine with a nearly identical 64-bit lucid configuration which also went through an update this morning, but without issue.  Further, on the second machine, gdb does not display the "CRC mismatch" error.  So far, I haven't been able to determine a difference between the two machines that might help me solve this problem.

Can anyone offer me advice on this?

Thanks in advance,
Dave Riesz

---

### Post by driesz on 2011-11-08
Well, it looks like a reboot took care of it.  Mysterious!

Dave Riesz

---

### Post by Paddy Landau on 2011-11-09
Most curious. I'm glad it is solved now.

---

### Post by driesz on 2011-11-09
It looks like it had something to do with qemu-kvm kernel modules.  I also have VirtualBox installed, and when VB tried to run a machine it encountered the already insmodded kvm and kvm_intel modules and then 32-bit binaries stopped working.  As soon as I disabled the qemu-kvm modules, the problem was fixed.

Dave Riesz

---


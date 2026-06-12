---
title: "crashdump fails"
date: 2010-11-28
forum: General Help
---

### Post by ppickfor on 2010-11-28
Hi All,

Ive tried to produce a crash dump from a fresh install of 64bit ubuntu 10.10.

I have crashkernel installed and the parameters in grub
but the machine will not respond to a crash request.

echo 1 > /proc/sys/kernel/panic_on_oops
echo c > /proc/sysrq-trigger

produces the attached on the console.

This works with 32bit ubuntu and a the crashkernel starts and the dump is recovered on the next boot.

Is does not work on 64bit on my laptop or mythtv or another 64bin machine or a fresh vm.

Any ideas much appreciated.

Thanks

Peter

---


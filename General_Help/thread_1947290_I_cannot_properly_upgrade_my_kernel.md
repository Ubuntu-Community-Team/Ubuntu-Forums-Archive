---
title: "I cannot properly upgrade my kernel"
date: 2012-03-26
forum: General Help
---

### Post by Lrno on 2012-03-26
Hello all, 

Well my problem is a bit strange. I am currently using Natty on a Samsung NC-110 netbook and it is working neatly using kernel **2.6.39-020639rc4-generic**.
Problem is, I've tried to upgrade to kernel **3.2.12-030212-generic** and the OS won't boot anymore. It gets stuck when the screen goes black just before the ubuntu banner shows up.

I have to confess that I am fairly new to ubuntu but I have been using it for quite some time already and I thought that kernel upgrading was a quite "safe" procedure.

In any case I will explain the procedure I have used in case I am doing something wrong.


[LIST=1]
[*]Download kernel files from [http://kernel.ubuntu.com/~kernel-ppa/mainline/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/")
[*]After downloading all 3 files, I open a terminal
[*]As a root I run: 
```
dpkg -i linux-headers-3.2.12-030212_3.2.12-030212.201203191306_all.deb
```After that:
```
dpkg -i linux-headers-3.2.12-030212-generic_3.2.12-030212.201203191306_amd64.deb
```And finally:
```
dpkg -i linux-image-3.2.12-030212-generic_3.2.12-030212.201203191306_amd64.deb
```
[*]```
reboot
```
[/LIST]
And it gets stuck, so I have to force a reset and boot with a previous kernel-image. Strange thing is that if I only install the linux-image and not the headers, I can boot kernel 3.2.12 no problem, but as soon as I install the linux-headers it gets stuck.

Any thoughts on the matter will be wonderful, remember I am still learning a lot from this great OS. 
And thanks in advance for any comment.

Cheers.
Lrno.

---


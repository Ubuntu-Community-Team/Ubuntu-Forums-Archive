---
title: "Segmentation fault with programs"
date: 2011-01-13
forum: General Help
---

### Post by obbe on 2011-01-13
Hi, I randomly get various segmentation faults when using my computer, it happens with almost every program, these are a few logs of what I get: 

```
nautilus[1973]: segfault at 558b0451 ip b729de6a sp bfb2e4f0 error 6 in libgdk-x11-2.0.so.0.2200.0[b7273000+94000]
chromium-browse[12443]: segfault at 74 ip b42463a7 sp a88baff0 error 4 in libnss3.so[b421e000+10c000]
rhythmbox[2065]: segfault at 571de000 ip b67be755 sp bfc17a18 error 4 in libc-2.12.1.so[b674a000+157000]
```

I run memtest86 but it didn't find any ram errors so I really don't know what the cause of the segmentation faults could be, this is my hardware configuration:

mobo: ASRock AM3 890GX Extreme3
cpu: AMD Phenom II X4
ram: Corsair Value Select 4gb (2+2)
primary hard drive: ocz ssd 120gb
secondary hard drive: western digital hard disk

Can anyone help me please? Thanks.. :(

---

### Post by Konstantin Dzreyev on 2011-01-13
yep, I see the same issue since todays update. Ruby interpreter and git started to expose the "Segmentation fault" error

Ubuntu 10.10 (64bit)
ProBook 4310s (ram:6GB(4+2), hdd:320GB(Hitachi HTS723232L))

---

### Post by tomapirin on 2011-08-05
Hello, any solution yet?

---

### Post by Entilza on 2011-08-05
I've noticed reports of segfault with newer kernels.  I believe the segfaults always happened before they just were not being recorded in the log files.

I basically reproduced it because I can segfault one particular application and it was not recorded with earlier kernel versions but with new kernels it was logged.

It's more of a annoyance to see the log file /var/log/messages with this warning.

If your programs are actually terminating unexpectedly then that is a little more of a problem than I mentioned above and could be hardware related...

---


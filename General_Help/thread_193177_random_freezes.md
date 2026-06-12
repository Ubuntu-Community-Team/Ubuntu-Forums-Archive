---
title: "random freezes"
date: 2006-06-09
forum: General Help
---

### Post by kevlarman on 2006-06-09
I recently installed ubuntu on my computer, for a while it worked fine, then it started randomly freezing (sometimes as soon as I log in, sometimes up to a couple hours after). I've tried everything I can think of and still can't figure it out](*,).

hardware:
pentium 3 500 mhz
nvidia geforce2 (installing nvidias driver fixed the problem for a bit, but then it came back)

i don't believe it's a hardware problem because before installing ubuntu, fedora worked just fine.

---

### Post by nanotube on 2006-06-09
[QUOTE=kevlarman]I recently installed ubuntu on my computer, for a while it worked fine, then it started randomly freezing (sometimes as soon as I log in, sometimes up to a couple hours after). I've tried everything I can think of and still can't figure it out](*,).

hardware:
pentium 3 500 mhz
nvidia geforce2 (installing nvidias driver fixed the problem for a bit, but then it came back)

i don't believe it's a hardware problem because before installing ubuntu, fedora worked just fine.[/QUOTE]
hmm well, a lot of random freezing has to do with video drivers... are you rinning on the stock nv driver, or did you install the official nvidia binaries?

another thing to check is to run a memtest. i know you said that fedora ran fine.. but a memtest never hurt anybody. :)

---

### Post by kevlarman on 2006-06-09
it freezes with both the nv driver and nvidia's drive, though like i said nvidia's driver seemed to make it better for a while. the memtest was one of the first parts of "everything I could think of"

---

### Post by kevlarman on 2006-06-09
anyone? I like ubuntu way too much to go back to fedora, but this make the system unusable

---

### Post by nanotube on 2006-06-09
[QUOTE=kevlarman]anyone? I like ubuntu way too much to go back to fedora, but this make the system unusable[/QUOTE]
anything in your logs?

---

### Post by kevlarman on 2006-06-09
which logs specifically?

i found this in /var/log/messages in several places (this is followed shortly by Kernel command line: root=/dev/hda1 ro quiet splash):
```

Jun  9 11:43:12 Roman kernel: [  165.518369]  [bad_page+93/176] bad_page+0x5d/0xb0
Jun  9 11:43:12 Roman kernel: [  165.518427]  [free_hot_cold_page+56/288] free_hot_cold_page+0x38/0x120
Jun  9 11:43:12 Roman kernel: [  165.518471]  [zap_pte_range+288/672] zap_pte_range+0x120/0x2a0
Jun  9 11:43:12 Roman kernel: [  165.518527]  [unmap_page_range+226/304] unmap_page_range+0xe2/0x130
Jun  9 11:43:12 Roman kernel: [  165.518619]  [unmap_vmas+190/528] unmap_vmas+0xbe/0x210
Jun  9 11:43:12 Roman kernel: [  165.518692]  [unmap_region+128/288] unmap_region+0x80/0x120
Jun  9 11:43:12 Roman kernel: [  165.518912]  [do_munmap+175/240] do_munmap+0xaf/0xf0
Jun  9 11:43:12 Roman kernel: [  165.518985]  [sys_munmap+58/96] sys_munmap+0x3a/0x60
Jun  9 11:43:12 Roman kernel: [  165.519028]  [sysenter_past_esp+84/121] sysenter_past_esp+0x54/0x79
Jun  9 11:43:50 Roman kernel: [  203.503879]  [bad_page+93/176] bad_page+0x5d/0xb0
Jun  9 11:43:50 Roman kernel: [  203.503939]  [free_hot_cold_page+56/288] free_hot_cold_page+0x38/0x120
Jun  9 11:43:50 Roman kernel: [  203.503984]  [zap_pte_range+288/672] zap_pte_range+0x120/0x2a0
Jun  9 11:43:50 Roman kernel: [  203.504042]  [unmap_page_range+226/304] unmap_page_range+0xe2/0x130
Jun  9 11:43:50 Roman kernel: [  203.504107]  [unmap_vmas+190/528] unmap_vmas+0xbe/0x210
Jun  9 11:43:50 Roman kernel: [  203.504178]  [unmap_region+128/288] unmap_region+0x80/0x120
Jun  9 11:43:50 Roman kernel: [  203.504246]  [do_munmap+175/240] do_munmap+0xaf/0xf0
Jun  9 11:43:50 Roman kernel: [  203.504317]  [sys_munmap+58/96] sys_munmap+0x3a/0x60
Jun  9 11:43:50 Roman kernel: [  203.504360]  [sysenter_past_esp+84/121] sysenter_past_esp+0x54/0x79
Jun  9 11:43:50 Roman kernel: [  203.504505]  [bad_page+93/176] bad_page+0x5d/0xb0


```

---

### Post by kevlarman on 2006-06-10
I just tried installing a trio video card that was lying around, and ubuntu stopped freezing, so the problem is almost certainly the video driver (the nvidia card works fine with other distro's). also, before anyone says just use this card, I need to have hardware opengl working.

---

### Post by tseliot on 2006-06-10
Are you sure that your card doesn't require the Nvidia Legacy driver?

Have a look at my guide, please:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper]("http://doc.gwos.org/index.php/Latest_Nvidia_Dapper")

---

### Post by kevlarman on 2006-06-10
first of all: ignore what I said about other cards, it still freezes, it just  took a bit longer than usual.
second: I checked, according to nvidia's site, the Geforce 2 MX 400 is supported

---

### Post by nanotube on 2006-06-10
[QUOTE=kevlarman]first of all: ignore what I said about other cards, it still freezes, it just  took a bit longer than usual.
second: I checked, according to nvidia's site, the Geforce 2 MX 400 is supported[/QUOTE]
well... this is not encouraging, but according to this: [http://forum.censornet.com/viewtopic.php?t=1134&sid=7297e05d5b437a6d69ac14ffc7f5e778](http://forum.censornet.com/viewtopic.php?t=1134&sid=7297e05d5b437a6d69ac14ffc7f5e778)
it may just be a bug in the kernel... i would advise to do some more research on google about kernel and bad_page and see if you can find any resolution... or just recompile your own kernel and see if that solves anything.

---

### Post by _simon_ on 2006-06-11
Do you dual boot at all with another OS? - if so can you boot into the other OS and see if you experience the "freeze"

From past experiences a dying PSU and excessive heat within the case can also freeze the system.

---

### Post by kevlarman on 2006-06-11
I recently replaced a dying psu, but fedora ran fine on it. Right now I'm using Knoppix 3.4 to post on the forums and google for information, and it never freezes.

---

### Post by kevlarman on 2006-06-15
using the vesa driver seems to solve the problem, but that's only a temperary solution because i do development in opengl. anyone have any idea's on how to get the nvidia driver working?

---


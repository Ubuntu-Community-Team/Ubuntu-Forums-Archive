---
title: "Computer's been randomly crashing, Think GPU's causing it."
date: 2012-08-05
forum: General Help
---

### Post by Dr Belka on 2012-08-05
Hey guys, little problem here.  My computer's been acting up lately.  The desktop will randomly become unresponsive, but the mouse will still move, and the sound is still playing.  I am unable to switch TTY's.  

Heres my /var/log/kern.log from the crash: ```
Aug  5 12:48:42 HADES kernel: [  446.090420] type=1701 audit(1344185322.651:37): auid=4294967295 uid=1000 gid=1000 ses=4294967295 pid=2878 comm="chrome" reason="seccomp" sig=0 syscall=83 compat=0 ip=0x7f549d015e47 code=0x50002
Aug  5 12:48:42 HADES kernel: [  446.090437] type=1701 audit(1344185322.651:38): auid=4294967295 uid=1000 gid=1000 ses=4294967295 pid=2878 comm="chrome" reason="seccomp" sig=0 syscall=83 compat=0 ip=0x7f549d015e47 code=0x50002
Aug  5 12:48:50 HADES kernel: [  454.105377] type=1701 audit(1344185330.667:39): auid=4294967295 uid=1000 gid=1000 ses=4294967295 pid=2878 comm="chrome" reason="seccomp" sig=0 syscall=83 compat=0 ip=0x7f549d015e47 code=0x50002
Aug  5 12:48:50 HADES kernel: [  454.105391] type=1701 audit(1344185330.667:40): auid=4294967295 uid=1000 gid=1000 ses=4294967295 pid=2878 comm="chrome" reason="seccomp" sig=0 syscall=83 compat=0 ip=0x7f549d015e47 code=0x50002
Aug  5 12:49:17 HADES kernel: [  480.458664] usb 2-1.4: new high-speed USB device number 4 using ehci_hcd
Aug  5 12:49:17 HADES kernel: [  480.579629] scsi10 : usb-storage 2-1.4:1.2
Aug  5 12:49:17 HADES kernel: [  480.584658] cdc_acm 2-1.4:1.0: This device cannot do calls on its own. It is not a modem.
Aug  5 12:49:17 HADES kernel: [  480.584722] cdc_acm 2-1.4:1.0: ttyACM0: USB ACM device
Aug  5 12:49:17 HADES kernel: [  480.585703] usbcore: registered new interface driver cdc_acm
Aug  5 12:49:17 HADES kernel: [  480.585705] cdc_acm: USB Abstract Control Model driver for USB modems and ISDN adapters
Aug  5 12:49:18 HADES kernel: [  481.591540] scsi 10:0:0:0: Direct-Access     SAMSUNG  SPH-D700 Card         PQ: 0 ANSI: 2
Aug  5 12:49:18 HADES kernel: [  481.592044] sd 10:0:0:0: Attached scsi generic sg10 type 0
Aug  5 12:49:18 HADES kernel: [  481.597020] sd 10:0:0:0: [sdj] Attached SCSI removable disk
Aug  5 13:34:58 HADES kernel: [ 3221.433560] type=1701 audit(1344188098.339:41): auid=4294967295 uid=1000 gid=1000 ses=4294967295 pid=2878 comm="chrome" reason="seccomp" sig=0 syscall=83 compat=0 ip=0x7f549d015e47 code=0x50002
Aug  5 13:34:58 HADES kernel: [ 3221.433567] type=1701 audit(1344188098.339:42): auid=4294967295 uid=1000 gid=1000 ses=4294967295 pid=2878 comm="chrome" reason="seccomp" sig=0 syscall=83 compat=0 ip=0x7f549d015e47 code=0x50002
Aug  5 14:53:16 HADES kernel: [ 7919.324139] NVRM: GPU at 0000:02:00.0 has fallen off the bus.

```

I see something about the GPU falling off the bus.  I don't know what that means, but I feel like it's significant.  

Does anyone have any ideas?

---

### Post by dcstar on 2012-08-06
> **Dr Belka said:**
> Hey guys, little problem here.  My computer's been acting up lately.  The desktop will randomly become unresponsive, but the mouse will still move, and the sound is still playing.  I am unable to switch TTY's.  

Heres my /var/log/kern.log from the crash: ```

.........
Aug  5 14:53:16 HADES kernel: [ 7919.324139] NVRM: GPU at 0000:02:00.0 has fallen off the bus.

```

I see something about the GPU falling off the bus.  I don't know what that means, but I feel like it's significant.  

Does anyone have any ideas?

There's this thing called Google which gave ME this after 30 seconds of searching:

[http://www.cyberciti.biz/faq/debian-ubuntu-rhel-fedora-linux-nvidia-nvrm-gpu-fallen-off-bus/](http://www.cyberciti.biz/faq/debian-ubuntu-rhel-fedora-linux-nvidia-nvrm-gpu-fallen-off-bus/)

---

### Post by efflandt on 2012-08-06
Sounds like a problem I had with my GT 430 from a Chinese company (Galaxie).  It worked fine for its one year warranty, but then started having some issues in Win7 where it would freeze and then say something about "recovered from video driver not responding", and updating drivers did not help.  In Ubuntu 11.10 the screen would occasionally freeze with no response to keyboard or mouse clicks, even though mouse cursor would usually still move.  It did not seem to happen in 10.10, maybe because I was just testing for short periods, but then it happened in 10.10 too.  Since it suddenly happened with no changes in multiple operating systems that it had worked in before, I consider that video card dead.  All operating systems 64-bit.

I have had no trouble with EVGA GTX 550 Ti, other than figuring out under which conditions **nomodeset** was necessary (not necessary for 10.10, necessary for installed 11.10, necessary during 12.04 install, but not for installed 12.04).  EVGA has 3 year warranty.

---

### Post by Dr Belka on 2012-08-06
> **dcstar said:**
> There's this thing called Google which gave ME this after 30 seconds of searching:

[http://www.cyberciti.biz/faq/debian-ubuntu-rhel-fedora-linux-nvidia-nvrm-gpu-fallen-off-bus/](http://www.cyberciti.biz/faq/debian-ubuntu-rhel-fedora-linux-nvidia-nvrm-gpu-fallen-off-bus/)

Thank you for your reply.  I found and tried that solution before ever I made this post.  Maybe I should have googled for at least 45 seconds?

> **efflandt said:**
> Sounds like a problem I had with my GT 430 from a Chinese company (Galaxie).  It worked fine for its one year warranty, but then started having some issues in Win7 where it would freeze and then say something about "recovered from video driver not responding", and updating drivers did not help.  In Ubuntu 11.10 the screen would occasionally freeze with no response to keyboard or mouse clicks, even though mouse cursor would usually still move.  It did not seem to happen in 10.10, maybe because I was just testing for short periods, but then it happened in 10.10 too.  Since it suddenly happened with no changes in multiple operating systems that it had worked in before, I consider that video card dead.  All operating systems 64-bit.

I have had no trouble with EVGA GTX 550 Ti, other than figuring out under which conditions **nomodeset** was necessary (not necessary for 10.10, necessary for installed 11.10, necessary during 12.04 install, but not for installed 12.04).  EVGA has 3 year warranty.

This is pretty much exactly what I've been experiencing, different problems depending on the OS, even between different versions of Ubuntu.  I'll play with the nomodeset and potentially swap in another graphics card to see if that takes care of my problems.

---

### Post by ottadini on 2012-11-18
>   I'll play with the nomodeset and potentially swap in another graphics card to see if that takes care of my problems.

So... did you do this? Did it take care of your problems?

---


---
title: "after updating to 3.3.4, no wifi (broadcom)"
date: 2012-05-07
forum: General Help
---

### Post by anoy20 on 2012-05-07
hi guys
I am using lubuntu 12.04
I downloaded the kernel in [http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.3.4-precise/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.3.4-precise/)
and I have sucessfully installed it

But after reboot, I find out that wifi disappear
and I press the panel network icons on top right hand, and only show LAN but no wifi


my network card is broadcom 4312
what problem is it?:confused:

---

### Post by carl4926 on 2012-05-07
If you were using the 'wl' driver, it won't work now.
You should remove it and use b43

---

### Post by anoy20 on 2012-05-07
thx carl4926,
I am newbie of linux and I have installed broadcom STA driver
is it b43?

---

### Post by Bucky Ball on 2012-05-07
Nope. You need to install b43-fwcutter and firmware-b43-installer through software centre or like so:

```
sudo apt-get install  b43-fwcutter firmware-b43-installer
```... then reboot. Think you might need to uninstall the STA driver before doing this but not positive. I would.

---

### Post by anoy20 on 2012-05-07
thx Bucky Ball,

I have tried your solution afer installing b43,
wifi can detect the hotspot but cannot connect
This situation is just the same as I flesh installed the ubuntu with default driver

seems only STA driver get me work 
but in kernel 3.3 it doestn't:(

---

### Post by carl4926 on 2012-05-07
The proprietary driver will not work with your custom kernel.
In any case you can use b43 which will work with any kernel 3> with your hardware.

But, if the proprietary driver is still installed, even if it's not working, it will prevent b43 from working because it adds a blacklisting for b43. So remove the proprietary driver to remove the blacklisting.

---

### Post by anoy20 on 2012-05-07
I have removed STA driver before installing b43
is it ok?

I still cannot get wifi work

---

### Post by carl4926 on 2012-05-07
```
sudo modprobe -rv b43
```
```
sudo modprobe -v b43
```

or just use the default system kernel as you were before

---

### Post by anoy20 on 2012-05-07
I am back to 3.2.0.24
but when I try to install STA driver, it fails and tells me to look at jockey.log


and here are the code

2012-05-07 23:08:00,801 DEBUG: BroadcomWLHandler enabled(): kmod disabled, bcm43xx: blacklisted, b43: blacklisted, b43legacy: blacklisted
2012-05-07 23:08:00,876 DEBUG: fglrx.enabled(fglrx): target_alt None current_alt /usr/lib/i386-linux-gnu/mesa/ld.so.conf other target alt None other current alt None
2012-05-07 23:08:00,877 DEBUG: fglrx is not the alternative in use

related to modprobe?

---

### Post by Bucky Ball on 2012-05-08
Don't try STA again. You are recreating the issue. After uninstalling that or a fresh kernel you should go directly for the b43 drivers/firmware. ;)

Give us the output of:

```
sudo lshw -C network

```
... and, just for luck, the output of:

```
iwconfig
```

Cheers. Please post here between code tags, the # sign if you 'Go Advanced'.

---

### Post by TBABill on 2012-05-08
Have you tried ```
sudo apt-get install --reinstall bcmwl-kernel-source
```And when it finishes just ```
sudo modprobe wl
``` No reason the proprietary driver should not work beautifully with the OP's BCM4312 and the stock kernel. I always use the STA on my 4312 devices instead of the b43.

---

### Post by anoy20 on 2012-05-08
thank you two guys
I reinstalled my ubuntu this morning](*,)
and I can almost confirm b43 won't work on 4312 just as TBABill said

So, I think I hv better stay in kernel 3.2 with STA
thx again for your kindly help:p

---

### Post by Bucky Ball on 2012-05-08
> **TBABill said:**
> Have you tried ```
sudo apt-get install --reinstall bcmwl-kernel-source
```And when it finishes just ```
sudo modprobe wl
``` No reason the proprietary driver should not work beautifully with the OP's BCM4312 and the stock kernel. I always use the STA on my 4312 devices instead of the b43.

All good, but .... have you tried it with 12.04 and this kernel? ;)

---

### Post by TBABill on 2012-05-08
Indeed I have, assuming by your question was regarding the stock 12.04 kernel since that's what I mentioned worked fine. I was not suggesting it should work great with a newly compiled kernel. I even activated it during the live session right from the DVD just to be sure it would work like always. I activate it via the GUI, then instead of restarting as it tells me to, I just ```
sudo modprobe wl
```Works like a charm. The BCM4311 is the device that is broken with the STA driver in Ubuntu, not the 4312.

---


---
title: "Ultra High CPU temperature on Natty"
date: 2011-04-28
forum: General Help
---

### Post by cokicd on 2011-04-28
Well, today I've installed 11.04 on my laptop. Fresh install.
I'm getting the following temps (idle)

```
Adapter: Virtual device
temp1:       +64.0°C  (crit = +126.0°C)                  

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +81.0°C  (high = +100.0°C, crit = +100.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +82.0°C  (high = +100.0°C, crit = +100.0°C)  

```This is really odd, my temps on lucid where about 48 to 52 °C (idle) on each core
What's happening? Any ideas?

---

### Post by mdurham on 2011-04-28
Maybe you need to do "sudo sensors-detect"

---

### Post by cokicd on 2011-04-28
> **mdurham said:**
> Maybe you need to do "sudo sensors-detect"

That was the first thing I did

---

### Post by KegHead on 2011-04-28
Hi!

You're a long way from critical


Adapter: Virtual device
temp1:       +64.0°C  (crit = +126.0°C)                  

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +81.0°C  (high = +100.0°C, crit = +100.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +82.0°C  (high = +100.0°C, crit = +100.0°C)

upgrading your kernel would/could help.

KegHead

---

### Post by Kvikvendi on 2011-04-29
I am experiencing the same issue. Of course I blamed Unity at first, but switching to Unity2D or classic Gnome doesn't help.

It's not so much a matter of really reaching critical levels or not (although the system comes too close for comfort when actually doing stuff), but the resulting noisy fan and hot lap are deal breakers...

---

### Post by Vaphell on 2011-04-29
recently there were reports of some regressions in the kernel which cause laptops to run out of juice much faster. Maybe it's related, after all energy usage and heat output go hand in hand.
[http://www.phoronix.com/scan.php?page=article&item=linux_kernel_regress2&num=1](http://www.phoronix.com/scan.php?page=article&item=linux_kernel_regress2&num=1)

---

### Post by antaios256 on 2011-04-29
> **Vaphell said:**
> recently there were reports of some regressions in the kernel which cause laptops to run out of juice much faster. Maybe it's related, after all energy usage and heat output go hand in hand.
[http://www.phoronix.com/scan.php?page=article&item=linux_kernel_regress2&num=1](http://www.phoronix.com/scan.php?page=article&item=linux_kernel_regress2&num=1)
this makes me feel better i was getting concerned about how hot my laptop was getting for the last few weeks. and I was expecting my hardware to be dying..but knowing its a kernel issue and can be fixed makes me happier

---

### Post by KegHead on 2011-04-29
Hi!

Update your kernel:

sudo apt-get update

sudo apt-get install linux-image -f

Restart

KegHead

---

### Post by cokicd on 2011-04-29
> **KegHead said:**
> Hi!

Update your kernel:

sudo apt-get update

sudo apt-get install linux-image -f

Restart

KegHead

I'm trying this now

---

### Post by cokicd on 2011-04-29
> **KegHead said:**
> Hi!

Update your kernel:

sudo apt-get update

sudo apt-get install linux-image -f

Restart

KegHead

It didn't work. Same temps.
Also I'm having some other problems
1) I can't connect to my wifi network most of the times. Sometimes it works.
2) The sound card (Sigmatel STAC9228) doesn't work. I get only dummy output under sound settings.

---

### Post by KegHead on 2011-04-29
Hi!

Some basics:

system...admin...additional drivers (install if needed)


system...preferences...sound


KegHead

---

### Post by cokicd on 2011-04-29
> **KegHead said:**
> Hi!

Some basics:

system...admin...additional drivers (install if needed)


system...preferences...sound


KegHead

Yes, I knew about that, the broadcom wireless driver is installed. I can see the wifi networks, but it keeps trying to connect forever. As I said, sometimes it works.
About the sound preferences, there is not much to see there, under hardware tab, it shows nothing, and under output tab, it shows dummy output.

---

### Post by Kvikvendi on 2011-04-29
Also did a kernel update, temperature seems unchanged. I guess we'll just have to wait for [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/760131](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/760131) to be solved and see if it is the same issue...

---

### Post by wingnux on 2011-04-29
Same thing happening here, last night my pc shut down twice because processor temperature was about 100o C =/

---

### Post by cokicd on 2011-04-29
I've reinstalled lucid. I think I'll keep it for a while

---

### Post by Lergus on 2011-05-04
Just load previous kernel, it helped for me.

---

### Post by me_loco on 2011-05-31
> **KegHead said:**
> Hi!

Update your kernel:

sudo apt-get update

sudo apt-get install linux-image -f

Restart

KegHead

do we have to manually update the kernel?

Thanks,

---


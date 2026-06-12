---
title: "Where is hw_random (hardware rng driver) on Karmic ?"
date: 2010-04-09
forum: General Help
---

### Post by scotty64 on 2010-04-09
I am interested in using the hardware RNG if present. As far as I know the driver is a module called hw_random, but modprobe does not offer any hw_random module in Karmic.
Has hardware RNG support being removed from the Karmic kernel or is it monolithically built into the Kernel ?
Thanks for any help.

---

### Post by undecim on 2010-04-09
Do you have a hardware RNG?

And have you isntalled rng-tools?

---

### Post by scotty64 on 2010-04-10
> **undecim said:**
> Do you have a hardware RNG?

And have you isntalled rng-tools?

I have an external hardware RNG (type "Orion", operated via serial port). This one works fine, but I would like to see if I can utilize the internal REG if present as well.
I am not sure if my machine has a built in hardware RNG, but the description for rng-tools points out that the hw_random module is needed. So there is still the question for me where hw_random is. It should be somewhere in the kernel tree - regardless if the functionality is there or not, but I cannot find it.

---

### Post by undecim on 2010-04-11
have a look at the output of
```
modprobe -l *-rng
```

It should list available rng drivers.

---

### Post by scotty64 on 2010-04-12
> **undecim said:**
> have a look at the output of
```
modprobe -l *-rng
```

It should list available rng drivers.

Thanks! I got this list:

kernel/drivers/char/hw_random/timeriomem-rng.ko
kernel/drivers/char/hw_random/intel-rng.ko
kernel/drivers/char/hw_random/amd-rng.ko
kernel/drivers/char/hw_random/geode-rng.ko
kernel/drivers/char/hw_random/via-rng.ko
kernel/drivers/char/hw_random/virtio-rng.ko

I tried the intel module, but got the "no such device" error. So my Dell XPS M1330 (Intel dual core CPU with Santa Rosa Chipset) does not seem to have a built-in hardware RNG. I wonder what the timeriomem-rng.ko and virtio-rng.ko modules provide and what hardware they need ?
I can load these modules without any errors, but no /dev/hwrng or similar device is created.

---


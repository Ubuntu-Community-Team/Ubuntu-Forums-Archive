---
title: "What command do I use to see my devices?"
date: 2009-12-07
forum: General Help
---

### Post by dpeizero on 2009-12-07
I'm looking for a terminal command or something that simulates the device manager for Windows. Anyone got any ideas?

Ubuntu 9.10 Karmic, if it matters.

---

### Post by SuperSonic4 on 2009-12-07
> **dpeizero said:**
> I'm looking for a terminal command or something that simulates the device manager for Windows. Anyone got any ideas?

Ubuntu 9.10 Karmic, if it matters.

```
lspci
```

if you want to be more specific ```
lspci | grep *whatever_you_are_searching_for*
```

for example for a video card ```
lspci | grep VGA
```

---

### Post by staf0048 on 2009-12-07
Without knowing what you're looking for, I'd try

```
lspci
```

The resulting screen can be somewhat cryptic..

Are you looking for something specific?

---

### Post by dpeizero on 2009-12-07
> **SuperSonic4 said:**
> ```
lspci
```if you want to be more specific ```
lspci | grep *whatever_you_are_searching_for*
```for example for a video card ```
lspci | grep VGA
```
Thanks. :D

---

### Post by t0p on 2009-12-07
There's also **lsusb** to show you usb devices.

To get a big list of just about *everything*, try:

```
sudo lshw
```

---


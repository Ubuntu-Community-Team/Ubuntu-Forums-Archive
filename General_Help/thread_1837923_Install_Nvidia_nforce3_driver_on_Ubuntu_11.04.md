---
title: "Install Nvidia nforce3 driver on Ubuntu 11.04"
date: 2011-09-02
forum: General Help
---

### Post by yura24 on 2011-09-02
Hi there,

is it possible?

couldnt find the driver for this Nvidia version.

I basically need to connect a second monitor and I was told installation of the driver should help.

any help appriciated

---

### Post by realzippy on 2011-09-02
Welcome..
..nforce3 is a (old) chipset for mainboards.
You mean **ge**force I guess.Open system=>administration=>additional drivers and check if there is a nvidia driver offered for your card.

---

### Post by yura24 on 2011-09-02
I checked with "hwinfo --pci" my system and I have Nvidia nforce3.

Is a newer driver like geforce compatyble with my hardware?

"system=>administration=>additional drivers" is empty

---

### Post by yura24 on 2011-09-02
I was able to connect the second monitor, but the screen resolution is not wide enough and despite of I set up both monitors to be synchron, no video playback on the second is possible.

is it a matter of a driver and if it is so which version should I install?

this question hopes to be resolved))

---

### Post by realzippy on 2011-09-03
please post output from

```
lspci |grep VGA
```

---

### Post by yura24 on 2011-09-03
here you go:

01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AP [Radeon 9600]

---

### Post by realzippy on 2011-09-03
You see?
You have an ATI graphics card,not an nvidia.
Nforce3 is the nvidia mainboard controller,which has nothing to do with your
graphics.
Back to topic:
There is no ATI graphics driver you could install besides the one which is already (and automatically) installed for your card.
ATI dropped Linux support for older cards a few years ago,sorry.

---


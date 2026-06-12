---
title: "Kernel 2.6.32-33 and Elantech touchpad"
date: 2011-07-15
forum: General Help
---

### Post by mikewhatever on 2011-07-15
Well, now the generic kernel 2.6.32-33.70 is out, the Elatech touchpad on my Dell Mini 10 is recognized properly, but is completely unusable. How do I configure it???

Edit: Simple. Add the following to startup apps:
```
synclient synclient TapButton2=2 TapButton3=3 AreaBottomEdge=670 AreaLeftEdge=50 AreaRightEdge=1100

```

Elantech touchpad recognized as Logitech mouse - kernel 2.6.32-32
```
I: Bus=0011 Vendor=0002 Product=0005 Version=0063
N: Name="ImPS/2 Logitech Wheel Mouse"
P: Phys=isa0060/serio1/input0
S: Sysfs=/devices/platform/i8042/serio1/input/input7
U: Uniq=
H: Handlers=mouse1 event6 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=103

```

Elantech touchpad recognized correctly - kernel 2.6.32-33
```
I: Bus=0011 Vendor=0002 Product=000e Version=0000
N: Name="ETPS/2 Elantech Touchpad"
P: Phys=isa0060/serio1/input0
S: Sysfs=/devices/platform/i8042/serio1/input/input10
U: Uniq=
H: Handlers=mouse1 event5
B: EV=b
B: KEY=6420 0 70000 0 0 0 0 0 0 0 0
B: ABS=f0003

```

---


---
title: "Advanced effects"
date: 2010-09-28
forum: General Help
---

### Post by NathanDTaylor on 2010-09-28
I forget the name exactly but the 3 settings for desktop effects won't enable. The only one that works is "off". Basic and Advanced both say "Could not be enabled" Or something like that.

It says my graphics card is "AMD M880G with ATI Mobility Radeon HD 4200".

Can anyone help me?

---

### Post by Ancanus on 2010-09-28
> **NathanDTaylor said:**
> I forget the name exactly but the 3 settings for desktop effects won't enable. The only one that works is "off". Basic and Advanced both say "Could not be enabled" Or something like that.

It says my graphics card is "AMD M880G with ATI Mobility Radeon HD 4200".

Can anyone help me?

You will need to install the proprietary drivers:

```
$sudo aptitude install fglrx
```

---

### Post by NathanDTaylor on 2010-09-28
then it should work?

```
nathan@NathanUbuntu:~$ sudo aptitude install fglrx
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done

```

"Desktop effects could not be enabled"

---

### Post by coolman98 on 2010-09-28
does it work?

---

### Post by NathanDTaylor on 2010-09-28
> **coolman98 said:**
> does it work?

no

"Desktop effects could not be enabled"

---

### Post by NathanDTaylor on 2010-09-28
bumppp

---

### Post by xJRBxJuggalo on 2010-09-28
```
mkdir -p ~/.config/compiz/ && echo SKIP_CHECKS=yes >> ~/.config/compiz/compiz-manager
```

---

### Post by NathanDTaylor on 2010-09-28
> **xJRBxJuggalo said:**
> ```
mkdir -p ~/.config/compiz/ && echo SKIP_CHECKS=yes >> ~/.config/compiz/compiz-manager
```

Desktop effects could not be enabled

---

### Post by IcewindDale on 2010-09-28
Try going into System->Administration->Hardware Drivers and see if you can activate any proprietary drivers there.

---

### Post by NathanDTaylor on 2010-09-28
I have already done this

---

### Post by NathanDTaylor on 2010-09-29
Any other suggestions?

---

### Post by Nerdfest on 2010-10-02
I have a G61 with (I think) the same card, and I have everything working using the xserver-xorg-video-radeonhd driver. Apparently it's development is pretty much at an end, but it works quite nicely. Remove the fglrx drivers.

---

### Post by distobj on 2010-10-17
Did you run "aticonfig --initial"?

---


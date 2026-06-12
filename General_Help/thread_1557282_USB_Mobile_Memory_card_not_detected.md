---
title: "USB Mobile Memory card not detected"
date: 2010-08-20
forum: General Help
---

### Post by satish_j on 2010-08-20
My system is able to detect normal USB drives(that are used for Data Storage),but is not able to detect USB mobile memory card..
THis is after i have freshly installed Hardy heron on new HD.On my old HD,it used to detect(auto-mount) memory card w/o any issues..
Any ideas what can be the possible cause??

---

### Post by madmax.santana on 2010-08-20
Is it a USB memory card reader? Because if it is, I am afraid Hardy might not have proper support for them.

---

### Post by satish_j on 2010-08-20
> **madmax.santana said:**
> Is it a USB memory card reader? Because if it is, I am afraid Hardy might not have proper support for them.
It is basically my Mobile containing the Memory card..
And,it was working fine on my OLd HD..On connecting my mobile phone to PC,memory Card used to get auto-mounted and a folder(of card reader) was opened directly..
BTW,i liked your Sig..;)

---

### Post by madmax.santana on 2010-08-21
> BTW,i liked your Sig..:wink: Tnx. You are the first person to say that. ;)

> And,it was working fine on my OLd HD..On connecting my mobile phone to  PC,memory Card used to get auto-mounted and a folder(of card reader) was  opened directly.. And which distribution/release is on your old HD? If it is a newer release than Hardy, there is a strong chance that hardy doesn't support that feature. And by the way, is your system up-to-date? You might need to upgrade your fstab and mount binaries.

---

### Post by satish_j on 2010-08-21
same distro on both Hds..i.e Hardy Heron
My system is also updated..
I would like to add here that the same prob is in XP also(am dual-mounting XP).In device manager(in XP),my mobile is selected with an Question mark,which cearly indicates that XP needs drivers for my mobile...

---

### Post by madmax.santana on 2010-08-21
Which mobile phone are you using?
Have you considered that maybe the data-cable has some fault? Or the pins / jacks need cleaning?
I owned Sony Ericsson w800 for quite some time. It has a pins-based plug and the cable port on the mobile phone often got coated with dust and needed cleaning. I just added some thinner on a cotton swab and cleaned the jack and it was working again...

When you connect the mobile to Ubuntu, what indication does it display? Does it indicate that the connection is established while in reality it is not?

---

### Post by satish_j on 2010-08-21
No,its not connection issues..
I do get output for command 'lsusb' as 
```

Bus 004 Device 002: ID 04e8:663e Samsung Electronics Co., Ltd 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

```

---

### Post by satish_j on 2010-08-23
Pls,someone help me..

---

### Post by satish_j on 2010-08-25
solved:D..it was the setting in my Cell phone that needs to be changed from 'PC suite' to 'Mass storage'..such a silly issue...

---


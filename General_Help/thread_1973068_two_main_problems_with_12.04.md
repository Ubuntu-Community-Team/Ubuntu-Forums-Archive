---
title: "two main problems with 12.04"
date: 2012-05-04
forum: General Help
---

### Post by wizard1983 on 2012-05-04
Shortly I have two main problems annoying me every time I try to use ubuntu  , 

1 - when I finish windows  installer and restart , I got no screen , and after many tries it works but not well as I expect 
2 - CPU fan speed works at its maximum speed all the time after log screen ( this since version 11.04)

any help would be appreciated

---

### Post by TenPlus1 on 2012-05-04
Post your laptop/computer type and specs, this will help a great deal...

---

### Post by wizard1983 on 2012-05-04
> **TenPlus1 said:**
> Post your laptop/computer type and specs, this will help a great deal...

MB : Gigabyte Ga-pa65-UD3-B3
CPU : Intel Core i5 2400
Display Adapter : ATI Radeon HD 6870

---

### Post by scalvo on 2012-05-04
> **wizard1983 said:**
> Shortly I have two main problems annoying me every time I try to use ubuntu  , 

1 - when I finish windows  installer and restart , I got no screen , and after many tries it works but not well as I expect 
2 - CPU fan speed works at its maximum speed all the time after log screen ( this since version 11.04)

any help would be appreciated

I have the same fan speed issue. Your first point, I think, have to do with your graphic card. Ati opensource drivers, no matter why they say about them, are crap. Ati propietary drivers are a lesser crap. If I were you, I would try the propietary drivers.

Look at the instructions here.
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

I tried both open-source and propietary drivers; all the solutions posted [here]("http://askubuntu.com/questions/116005/gnome-3-ati-fan-always-on"). 
None of them worked.

I tried fancontrol and pwmconfig but is says:

```
/usr/sbin/pwmconfig: There are no pwm-capable sensor modules installed
```I have an Asus I7 laptop with Ati Mobility Radeon 5730 and I can't control fan-speed through BIOS (there's no option to do it).

This issue is driving me crazy. Right now I have Windows 7, Ubuntu 10.10 (working perfectly) and Ubuntu 12.04 and I would like to stick to the last version but this fan issue is really anoying.

P.D Excuse my english :).

---

### Post by wizard1983 on 2012-05-04
> **scalvo said:**
> I have the same fan speed issue. Your first point, I think, have to do with your graphic card. Ati opensource drivers, no matter why they say about them, are crap. Ati propietary drivers are a lesser crap. If I were you, I would try the propietary drivers.

Look at the instructions here.
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

I tried both open-source and propietary drivers; all the solutions posted [here]("http://askubuntu.com/questions/116005/gnome-3-ati-fan-always-on"). 
None of them worked.

I tried fancontrol and pwmconfig but is says:

```
/usr/sbin/pwmconfig: There are no pwm-capable sensor modules installed
```I have an Asus I7 laptop with Ati Mobility Radeon 5730 and I can't control fan-speed through BIOS (there's no option to do it).

This issue is driving me crazy. Right now I have Windows 7, Ubuntu 10.10 (working perfectly) and Ubuntu 12.04 and I would like to stick to the last version but this fan issue is really anoying.

P.D Excuse my english :).


max Fan speed is really an annoying issue .   till now I can hardly solve Display problem ,  thank you Scalvo .

---


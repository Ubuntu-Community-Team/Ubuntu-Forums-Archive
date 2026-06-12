---
title: "(Wacom) Connect DTU-2231 to EB-460 Projector"
date: 2012-05-25
forum: General Help
---

### Post by vinterkind on 2012-05-25
Hi,

I've got a DTU-2231 interactive pen display connected to an ubuntu 12.04 machine. Everything works fine so far, but I want to use the tablet's DVI-I out Port. It should mirror the tablet's display to the projector/beamer whatever. The Manual simply says "Install all the drivers"  I compiled the wacom-drivers 0.9.3, and it still doesn't work. 

Any suggestions ?

---

### Post by Favux on 2012-05-26
Hi vinterkind,

> The Manual simply says "Install all the drivers" I compiled the wacom-drivers 0.9.3, and it still doesn't work. 
There is no 0.9.3 currently available for Ubuntu Precise (12.04).  That sounds like the linux-wacom-0.9.3 driver which is for kernels older than Lucids 2.6.32 kernel and X Servers older than Lucid's 1.7.  You shouldn't have been able to compile it in Precise.

I do not know if the xf86-input-wacom driver-0.14.0, default in Precise, supports the DTU-2231's DVI-I out Port.  The model is supported and it sounds like it is working.  Anyway you might have better luck asking the linuxwacom-discuss mailing list that question:  [https://lists.sourceforge.net/lists/listinfo/linuxwacom-discuss](https://lists.sourceforge.net/lists/listinfo/linuxwacom-discuss)

So the tablet has it's own built-in video card that can drive an external monitor or projector?  If so I tend to doubt the Wacom X driver handles that.  It would make more sense to me if it was suppose to go through the laptop, using the laptop's video card.  Then it is a question of configuring the laptop's video.

---

### Post by vinterkind on 2012-06-14
Hi favux!

> **Favux said:**
> 
There is no 0.9.3 currently available for Ubuntu Precise (12.04).  That sounds like the linux-wacom-0.9.3 driver which is for kernels older than Lucids 2.6.32 kernel and X Servers older than Lucid's 1.7.  You shouldn't have been able to compile it in Precise.

I do not know if the xf86-input-wacom driver-0.14.0, default in Precise, supports the DTU-2231's DVI-I out Port.  The model is supported and it sounds like it is working.  Anyway you might have better luck asking the linuxwacom-discuss mailing list that question:  [https://lists.sourceforge.net/lists/listinfo/linuxwacom-discuss](https://lists.sourceforge.net/lists/listinfo/linuxwacom-discuss)


You're right. It was an older package. To compile it though wasn't the problem. 
And yes it is working fine. I've got a dual-head display with the tablet bound to my left monitor. Works like a charm.

> **Favux said:**
> 
So the tablet has it's own built-in video card that can drive an external monitor or projector?  If so I tend to doubt the Wacom X driver handles that.  It would make more sense to me if it was suppose to go through the laptop, using the laptop's video card.  Then it is a question of configuring the laptop's video.

Well, the manual says

```
The pen display can be used alone or with another display. You may connect a second device, such
as a monitor or LCD projector, to the DVI-I OUT port. When using this port, the second device will
mirror the image on the pen display. Complete the pen display installation before connecting
another device to the unit.
```So I guess it should be possible ... 

Cheers,
vk

---


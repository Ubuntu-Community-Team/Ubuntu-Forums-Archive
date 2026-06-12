---
title: "ATI Driver Bug? Boot Res changed!"
date: 2010-05-04
forum: General Help
---

### Post by asn_knight on 2010-05-04
Well, I hav a ATI Radeon Moibility 3650. 
Last time in Karmic I had a probem with maximizing and minimizing 
windows. But I solved it using xorg-backfill from a ppa.
I had installed the ATI Driver which i got from ATI support website.
Well there was another problem then whch i never noticed. The ubuntu symbol which was appearin durin the boot up was not displayed correctly. Some resolution error. I never bothered to worry.

Now, I hav Lucid Lynx installed (clean installation). The display is too good without having installed the driver,
Extra visual effects could also be enabled wthout having to install the graphics driver. 
I installed the driver and then found a problem. Everthing works fine except the beautiful " ubuntu " written 
was displayed in very low res. Everythn was same except for that. The ATI FGLRX is bugged OR can I solve it changing the resolution in /etc/default/grub ?

Let me be clear in my question again :
If I installed my ATI driver in Lucid can I make the initial boot up screen to display as it was b4 installin the driver?

PS : My screen res is 1366x768. I dont think this is supported by VBE or sumthn ( I dunno abt it ) .

Thank You,

asn_knight

---

### Post by Amranu on 2010-05-04
The ATI Catalyst driver does not support KMS, and so the resolution does not automatically change to the proper resolution.

---

### Post by techunit on 2010-05-04
I had to deactivate the ATI driver. The open-source driver works fine.

---

### Post by metro23man on 2010-05-04
This driver caused me big problems also.  Laptop either locked up shorty after login and sometimes rebooted shortly after login.

Is there any way to get notification about updated ATI driver for Ubuntu?

---

### Post by asn_knight on 2010-05-12
@Amranu Is a update on its way?
@techunit Yeah. Open Source driver is fine, but i wanted hardware acceleration for a few apps. Couldnt use that. :(
@metro23man No. I dont think so. U may hav to ceck in ATI website each time. :(

---

### Post by japher on 2010-05-14
Does anyone know if this is something that can be patched, or fixed by a change to a conf file? Or is this something that can only be fixed by ATI?

Sad to lose my beautiful, crisp boot screen, but I just know I'll need hardware 3D acceleration now and then :(

---

### Post by CarpKing on 2010-06-06
Without a radical rewrite and change in design the proprietary drivers will never support KMS.  However, the open-source drivers do support 3d accel, so your card will be supported in time.

---


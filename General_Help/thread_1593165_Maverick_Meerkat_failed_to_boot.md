---
title: "Maverick Meerkat failed to boot"
date: 2010-10-11
forum: General Help
---

### Post by shahan on 2010-10-11
I am using Lucid for last 6 month and I am really amazing for its stability of using. And I am a Desktop user.
However, Yesterday I have downloaded the 10.10 Maverick Meerkat Desktop (32 Bit). I have made a Startup Disk using UBUNTU Startup Disk Creator for that .iso which I have downloaded yesterday. That is a USB Live Disk. 
But the sad news is its not being able to boot my PC. where my PC configuration is not so bad.
Pentium Dual Core E2200 @2.20 Ghz 
Gigabyte GA-G31M-ES2C motherboard
2GB DDR2 RAM with 800 bus speed
1TB HDD
(I also tried disconnecting the HDD and my DVD Rom, same problem arises)


The boot screen is trying to boot the PC but its doing for a long time, for about 10 mins, nothing reports it. I have press ESC to see wats happening beside this. Then I have seen a text there. Which is similar to the below (may have some spelling mistakes)
"Process 283 Glib warning getpwuid_r(): failed due to unknown user id (0)"

I hve checked the .iso SUM several times, where everything is ok.

---

### Post by dino99 on 2010-10-11
as you describe the problem, i'm thinking about a pci or acpi issue:

add either: noacpi, irqpoll, nomodeset, nolapic, noapic on the boot line

you might have burn the iso with the lowest speed too (usb-creator is the most recommended software)

---

### Post by shahan on 2010-10-11
>  add either: noacpi, irqpoll, nomodeset, nolapic, noapic on the boot lineHow to do that?

> you might have burn the iso with the lowest speed too (usb-creator is the most recommended software)It should be mentioned here that I have tried this same USB stick (with ubuntu installed using STARTUP DISK CREATOR) in two more computers. where it has performed well.

---

### Post by Chesamo on 2010-10-11
> **shahan said:**
> How to do that?
Once you're at the boot splash screen, hit F6 to bring up the Other Options menu.

---

### Post by shahan on 2010-10-11
> **Chesamo said:**
> Once you're at the boot splash screen, hit F6 to bring up the Other Options menu.
It replies the previous things Which occoured for pressing ESC.

---

### Post by shahan on 2010-10-12
> **dino99 said:**
> 
you might have burn the iso with the lowest speed too (usb-creator is the most recommended software)

I have burn the iso with 16x speed using Brasero. Now my PC has been booted. But its taking a long time then other computers (I have tried this .iso to other PC. But the specifications of these computer is about to same.

---


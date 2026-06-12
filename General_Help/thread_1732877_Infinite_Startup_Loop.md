---
title: "Infinite Startup Loop"
date: 2011-04-18
forum: General Help
---

### Post by cjosh on 2011-04-18
Hi I'm doing a dual boot Ubuntu 11.04 and Windows 7 on my Asus UL80v. When I restart and keep going into Ubuntu I'm fine, but I think if I go to Windows and then restart, the infinte start up happens, and I'm currently stuck in this.

It'll go to the OEM screen, then a black screen with a cursor, then it goes black, and then back to the OEM screen and so on and so forth.

I'm posting here because maybe something is happening to Grub? I'm not sure, and I'm not too experienced with it so I'd appreciate with any help.

Luckily I have Ubuntu 10 on my flash drive, so I'm booting to that while I try to figure out this.

...

Which reminds me, when I use the flash drive, there's an option to boot to local disk which also does not work, if that's worth anything. Before this happened, I ran check disk on windows because I ran into some partition troubles. There seemed to be no problems, and I can still access the drives from this flash Ubuntu.

---

### Post by dcstar on 2011-04-20
> **cjosh said:**
> Hi I'm doing a dual boot Ubuntu 11.04 and Windows 7 on my Asus UL80v. When I restart and keep going into Ubuntu I'm fine, but I think if I go to Windows and then restart, the infinte start up happens, and I'm currently stuck in this.

It'll go to the OEM screen, then a black screen with a cursor, then it goes black, and then back to the OEM screen and so on and so forth.

I'm posting here because maybe something is happening to Grub? I'm not sure, and I'm not too experienced with it so I'd appreciate with any help.

Luckily I have Ubuntu 10 on my flash drive, so I'm booting to that while I try to figure out this.

...

Which reminds me, when I use the flash drive, there's an option to boot to local disk which also does not work, if that's worth anything. Before this happened, I ran check disk on windows because I ran into some partition troubles. There seemed to be no problems, and I can still access the drives from this flash Ubuntu.

Quite possibly Windows is putting the video hardware into a mode that is not resetting when a reboot occurs, and when Ubuntu tries to load the video drivers don't work.

The USB stick boot won't be using the hardware video drivers, so try uninstalling the hardware video drivers from the main install and see if that fixes things.

If it does then file a bug report for those video drivers.

---


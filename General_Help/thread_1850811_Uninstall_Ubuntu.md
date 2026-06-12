---
title: "Uninstall Ubuntu"
date: 2011-09-27
forum: General Help
---

### Post by mac666 on 2011-09-27
Hello
I have one SSD disc partinoned into several partions:

Sda1 has Ubuntu 10.04
Sda6 has Ubuntu 10.10

I want to uninstall Ubuntu on Sda6.
How ever, i think the grub boots to Sda6, or something, there are grub on Sda1 and Sda6.

How would i do to uninstall Ubuntu on Sda6, and keeping grub alive and that i still will be able to boot into Sda1?

---

### Post by mastablasta on 2011-09-27
boot with liveCD and delete the sda6 partition using gparted. then update grub.

---

### Post by mac666 on 2011-09-27
> **mastablasta said:**
> boot with liveCD and delete the sda6 partition using gparted. then update grub.

Can i run update-grub från the live cd?

---

### Post by seawolf167 on 2011-09-27
You don't even need to boot to a LiveCD - just boot into /sda1 containing your 10.04 install, then open GParted and delete the partition /sda6 with it unmounted. You can then run

```
sudo update-grub
```from within your 10.04 install. Just incase something unexpected happens... reinstalling Grub2 is [super easy]("https://help.ubuntu.com/community/Grub2#Reinstalling_GRUB2").

---

### Post by mac666 on 2011-09-29
Actually, update-grub didnt work for me. Neither from the installation nor the live cd.
But with boot-repair, it worked!
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) 
I got the dropped to shell when trying to boot, "grub rescue>"
But all is OK now!

Thanks

---


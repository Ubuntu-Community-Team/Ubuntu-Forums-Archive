---
title: "How to manually set when battery power is critically low?"
date: 2011-11-26
forum: General Help
---

### Post by RonB123123 on 2011-11-26
Hi,

I have a laptop and whenever the battery dies with the laptop on, Ubuntu won't start up again due to file system errors. The only way to revive it is to put in the Ubuntu LiveCD or any Linux and run the following commands:

sudo umount /dev/sda1
sudo e2fsck -c /dev/sda1

This will take around an hour and a half for me and then Ubuntu will boot up fine. Since my computer turns off when the battery power is low (because I have that setting checked), it shuts it off at 5% battery remaining. When I forget that it only has 5% left and turn it back on, it comes on and instantly dies and I have to repeat the LiveCD method. 

So how do I manually set when the battery power is critically low? This way if I can set it to 15% remaining and turn it back on, it will still have enough energy for me to plug the computer back in.

Regards,

---

### Post by dcstar on 2011-11-26
> **RonB123123 said:**
> 
.........
So how do I manually set when the battery power is critically low? This way if I can set it to 15% remaining and turn it back on, it will still have enough energy for me to plug the computer back in.

Regards,

Gconf key: /apps/gnome-power-manager/thresholds/percentage_low

---


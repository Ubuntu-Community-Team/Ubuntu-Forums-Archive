---
title: "X Video Config/Help!"
date: 2010-09-07
forum: General Help
---

### Post by clayjackson on 2010-09-07
So - my motherboard died Friday, and I replaced it with a brand new ASUS board that has an Intel 4500 Graphics chipset.   

Now, when I boot; all I see on my monitor is it's "out of range" message.

I can ssh to the box just fine; but I'd really like to get X back up and running.

Is there an easy way to force ubuntu to regenerate all of the necessary config files.

Thanks in advance!

Clay Jackson
[EMAIL="clayj@nwlink.com"]clayj@nwlink.com[/EMAIL]

---

### Post by Vigh on 2010-09-07
Hope this helps, whenever there is a problem with the xorg-xserver display driver. All you have to do is hold down shift while the computer is initially booting, before anything loads, like when your bios display screen comes up, hold down shift and dont let go until you have a menu where you can select which kernel you want. You will then want to select kernel-xx.xx.xx.xx-recoverymode. A menu will come up then, and you can reconfigure graphics, just click restore default graphics, click okay and reboot and let it load normally, should fix your problem. Hope this helps.

---

### Post by clayjackson on 2010-09-07
Well, no joy on that - the shift key did nothing on my system; and when I go to the grub menu, there's no "reset graphics" option.

Still looking for a solution.....

---

### Post by no2498 on 2010-09-08
try the esc key
or just hard boot it

---

### Post by Vigh on 2010-09-09
what version of ubuntu are you using? intel graphics are not well supported by linux, the latest version 10.04 has reasonable generic opensource drivers however if you are using an old version it may not detect your graphics at all, the other option if you can get to the console, is to reconfigure the xserver-xorg

---


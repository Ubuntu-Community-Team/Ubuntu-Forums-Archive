---
title: "Deleted grub in win7 disk manager"
date: 2010-12-12
forum: General Help
---

### Post by sirg00se on 2010-12-12
So here's the deal. My tech savvy friends built me a computer and put win7 64 bit and then installed ubuntu (upgraded to 10.10) and had grub so whenever i turned my computer on i could choose between linux and windows and everything was fine. The other day i couldn't boot into ubuntu so i went into my win7 partition and deleted ubuntu and all other partitions and/or extensions thinking that it would get rid of ubuntu. Now when i boot it doesnt recognize anything so i tried booting from my ubuntu cd (don't know if its 10.4 or version) and it will load and when i try to install it i get the grub recovery thing and then the initramfs thing and the error "initramfs Can not mount /dev/loop0 (/live/image/live/filesystem.squashfs)"

i don't need ubuntu but i do need windows as it has files and papers that i need this week. 

what do i do?

---

### Post by drs305 on 2010-12-12
From the LiveCD, just to get Windows booting:

```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```

Don't worry about any of the lilo messages. Those are the only two commands you want to run. The second commands assumes your Windows install is on sda (first drive).

Once you get Windows back and have a few moments let us know when you want to restore Ubuntu.

---

### Post by Quackers on 2010-12-12
You need to run startup repair from the Windows repair disc (or installation disc) to fix the mbr.

Edit
Lol, drs305, or Lilo :-)

---

### Post by drs305 on 2010-12-12
> **Quackers said:**
> You need to run startup repair from the Windows repair disc (or installation disc) to fix the mbr.

Edit
Lol, drs305, or Lilo :-)

I normally recommend using Windows products to repair Windows, but if there is a boot flag on the proper partition and the Windows boot files aren't corrupt I don't think I've ever seen lilo fail.

---

### Post by Quackers on 2010-12-12
I can't argue with that :-)

---

### Post by sirg00se on 2010-12-13
when i'm in the liveCD how do i do that? i only have the choices of trying ubuntu, installing it, etc.

---

### Post by drs305 on 2010-12-13
> **sirg00se said:**
> when i'm in the liveCD how do i do that? i only have the choices of trying ubuntu, installing it, etc.


You select "Try Ubuntu", then when you get to the Desktop you open a terminal via Applications, Accessories, Terminal.

---

### Post by sirg00se on 2010-12-13
when i select "try ubuntu" thats when i get the "initramfs Can not mount /dev/loop0 (/live/image/live/filesystem.squashfs)" message.

---


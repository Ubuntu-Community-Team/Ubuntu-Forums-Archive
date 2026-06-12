---
title: "Dual Booting and HD Upgrade Problem"
date: 2006-06-08
forum: General Help
---

### Post by zenchili on 2006-06-08
Hi everyone, I'm fairly new to Ubuntu, I'm a long time Windows user, though as a kid I did have an Amiga. Anyway I'm on a desktop with 2 hard drives. The main one has my windows xp installation, and the second drive is devoted to ubuntu. When I installed ubuntu it put Grub into the MBR so now if I disconnect the Ubuntu drive the system can't boot, even into windows. I would like to upgrade my windows drive but I am not sure how to do it since I can't unplug the ubuntu drive and still boot into windows so I could use DriveCopy to move all my windows stuff to the new bigger drive (well, it will be bigger once I buy it).

I figured there might be a solution if I created a floppy boot disk that would allow me to start grub, even if the ubuntu drive was not connected. With grub active, I'd then hopefully be able to go into windows, do the Drive Copy thing, remove the now smaller windows hard drive and reconnect the ubuntu drive and have everything back to normal with a larger windows drive. Is this possible to do?

If it is possible, how do I go about doing this? Any and all help is greatly appreciated. Thanks,

Zen

---

### Post by slimdog360 on 2006-06-08
There is probably a better way but.. you should be able to install the new hdd and install windows onto that, you wont need the grub loader. Then once that is running copy over the hdd, then if you wanted format the old windows partion on your old hdd into a fat32 partion and use it to share files.
any questions you can pm me or leave another message.

---

### Post by elamericano on 2006-06-08
I would just get Windows booting on its own again. Strange that it doesn't work already, since GRUB overwrote the MBR of the other disk, not the Windows disk (unless you tried an install on the same disk at some point) Can you set the BIOS to boot your Windows disk first? If that doesn't work and something really has happened to your MBR, you can use the XP install CD to run recovery console (instead of installing). From the recovery console command line, "fixmbr" restores your MBR and allows you to boot Windows again. This wouldn't interfere with GRUB on the other disk. Whichever disk was set to boot first would load it's own bootloader.

---

### Post by zenchili on 2006-06-08
I figured out another way to do it...I had to reinstall Ubuntu, which luckily was not a big deal since I had only had it running for less than a day. This allowed me to select win xp at boot through grub (yes, somehow magically windows came back), and yes I could boot into windows. Then since I have 2 DVD drives (one's a writer) I can just disconnect one of those, connect the new hard drive to where a DVD drive was connected, do the drive copy thing to to copy the old drive to the new drive. Shut down, replace the old drive with the new drive, reconnect the DVD drive and we're off to the races. I must admit though I did get a bit freaked out when I couldn't boot back into windows, but reinstalling Ubuntu brought that back....Anyway, thanks for the help.

---


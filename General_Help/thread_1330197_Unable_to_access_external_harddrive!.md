---
title: "Unable to access external harddrive!"
date: 2009-11-18
forum: General Help
---

### Post by Zvenne on 2009-11-18
As the title says, I am unable to access my external harddrive. The problem first occured while running Windows XP, I plugged in the device just as I always have, but then nothing happened. Just the ordinary "alert sound" but no pop-up menu and no icon in "My Computer". 
So I tried to plug it in while in Ubuntu to see if I could access it that way. But it will not mount for me... I ran the cmd sudo fdisk -l and end up with this output: (It's in Swedish but I hope you get the point anyway)

```

Disk /dev/sda: 40,0 GB, 40007761920 byte
255 huvuden, 63 sektorer/spår, 4864 cylindrar
Enheter = cylindrar av 16065 · 512 = 8225280 byte
Diskidentifierare: 0x03910390

    Enhet Start     Början        Slut     Block    Id  System
/dev/sda1   *           1        4864    39070048+   7  HPFS/NTFS

Disk /dev/sdb: 80,0 GB, 80026361344 byte
255 huvuden, 63 sektorer/spår, 9729 cylindrar
Enheter = cylindrar av 16065 · 512 = 8225280 byte
Diskidentifierare: 0x55096fd8

    Enhet Start     Början        Slut     Block    Id  System


```The 40,0 GB HDD is my internal drive, and the other one 80,0 GB is the external so I guess it is not completely dead and I still got my hopes up.
So this is my problem. Is there anyway to maybe force it to mount? Or can I access it in any other way? I really want to backup what's on it so I don't really want to format it or anything like that so if that is avoidable it would be good.

I have searched the forum but haven't found any situation like mine and I also am kind of new to Ubuntu. If you need more information about the situation just ask and I'll try to provide it.

Thanks in advance!

---

### Post by P4man on 2009-11-18
Seems it lost its partition table. Try installing testdisk in ubuntu and run that. You can install testdisk through synaptic and extensive documentation can be found here:
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by Zvenne on 2009-11-18
Thanks for your reply P4Man, I will try yout suggestion and post my results!

---

### Post by Zvenne on 2009-11-18
I did as you said and downloaded TestDisk, and it worked out great! I was able to access all files from within the program and I ahve successfully copied all to my computer. Although how shall I proceed now in terms of making the HDD functioning normally again?

---

### Post by P4man on 2009-11-18
you could just create a fresh partition on it using gparted (or your preferred windows tool). But I would check the hardware first. If you are booting from a karmic cd, go to system > administration > disk utility and make sure the drive is healthy. Partition tables dont just disappear. Id guess its either a dying harddisk or a windows virus..

---

